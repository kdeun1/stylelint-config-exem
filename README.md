# stylelint-config-exem-frondend
- stylelint-config-exem은 exem css 컨벤션 lint 룰셋입니다.
- stylelint-config-exem은 [styleline-config-standard](https://github.com/stylelint/stylelint-config-standard)를 기준으로 작성되었으며, scss/order 관련 규칙을 추가하였습니다. 

## Install
```bash
npm install stylelint stylelint-config-exem --save-dev
```

## Usage
`stylelint.config.js` 파일을 루트 디렉토리에 생성해주세요
```javascript
module.exports = {
  extends: 'stylelint-config-exem',
  rules: {
    // 프로젝트 적용할 룰
  },
};
```

## EXEM CSS Style Guide
[CSS Style Guide](./STYLE-GUIDE.md)

## License
This software is licensed under the [MIT License](https://github.com/ex-em/stylelint-config-exem/blob/main/LICENSE).
