# ベースイメージとしてNode.jsを指定
FROM node:18

# 作業ディレクトリを作成
WORKDIR /app

# パッケージファイルをコピー
COPY package.json package-lock.json ./

# 依存関係をインストール
RUN npm install

# 残りのアプリケーションファイルをコピー
COPY . .

# TypeScriptのビルドを実行
RUN npm run build

# サーバーを起動
CMD ["npm", "start"]
