# 설명
- webpack
    - 여러 파일로 나뉜 자바스크립트파일들을 번들, 패킹하여 하나로 합쳐준는거
- babel
    - 최신버전의 자바스크립트를 호환가능하도록 변환
    - 전부는 아니저라도 일부 변환 가능한부분을 변환 해줌.(coverage가 있다.)
# 사용법
- webpack.config.js에서
    - `entry: ['@babel/polyfill', './main.js']`로 기준이 되는 main.js부터 impot된 모든 파일을 패키징한다.
- 빌드된 파일 위치
    - js
        - webpack.config.js의 output에 정의 되어있다.
        - ```json
            ...,
            output: {
                path: path.resolve(__dirname, 'dist'),//폴더명
                filename: 'js/bundle.js'//파일 이름
            },
            ...
         ```
    - css(webpack.config.js의 entry에 작성한경우)
        - sass로 작성후 빌드를 할경우 sass파일의 위치를 entry에 추가
            - ```json
              entry: ['@babel/polyfill', './main.js', './sass/main.scss'],
             ``` 
        - 저장위치는 webpack.config.js의 plugins에서 명시되어있음
            - ```json
                ...,
                plugins: [
                    // 컴파일 + 번들링 CSS 파일이 저장될 경로와 이름 지정
                    new MiniCssExtractPlugin({ filename: 'css/style.css' })
                ],
                ...
             ```
# 실행
- 빌드 수행
```
npm run build
```
- package.json에 명시되어있다.
```json
  ...,
  "scripts": {
    "build": "webpack -w"// 이게 실행됨
  },...
```

# 설치
## 바벨

- 기본
```
npm install --save-dev @babel/core @babel/cli 
```
- 환경
```
npm install --save-dev @babel/preset-env
```
- 플러그인(클래스)
```
npm install --save-dev @babel/plugin-proposal-class-properties
```
- webpack 연결시 사용
```
npm install --save-dev babel-loader 
```
- 브라우저 호환을 위해, 개발뿐만아니라 실제에서도 가능해야 함
```
npm install @babel/polyfill
```
- sass를 css로 빌드
```
npm install node-sass style-loader css-loader sass-loader --save-dev
```
- 플러그인(css를 별도로 저장)
```
npm install --save-dev mini-css-extract-plugin
```
## webpack
```
npm install --save-dev webpack webpack-cli webpack-dev-server
```


---
# 참고, 출처
https://poiemaweb.com/es6-babel-webpack-1
https://poiemaweb.com/es6-babel-webpack-2