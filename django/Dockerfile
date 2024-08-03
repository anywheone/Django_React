# ベースイメージとしてPythonを使用
FROM python:3.10-slim

# 作業ディレクトリを作成
WORKDIR /app

# 必要なPythonパッケージをインストールするためのファイルをコピー
COPY requirements.txt .

# Pythonパッケージのインストール
RUN pip install --no-cache-dir -r requirements.txt

# アプリケーションのソースコードをコピー
COPY . .

# 環境変数を設定
ENV DJANGO_SETTINGS_MODULE=myproject.settings
ENV PYTHONUNBUFFERED=1

# マイグレーションと静的ファイルの収集
RUN python manage.py migrate
RUN python manage.py collectstatic --noinput

# コンテナがリッスンするポートを指定
EXPOSE 8000

# アプリケーションを起動
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "myproject.wsgi:application"]
