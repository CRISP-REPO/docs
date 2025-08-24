# docs
1. vs Code 확장 호스트는 Node(Undici) 신뢰 스토어를 씁니다. 브라우저가 “예외적으로 허용”한 로컬 인증서를 Node는 여전히 불신합니다. 그래서 https://localhost를 사용하면 에러가 발생 => 로컬 서버의 인증성를 신뢰하도록 만들어야함.

2. mkcert로 “신뢰 가능한” 로컬 인증서 발급
      - brew install mkcert nss
      - mkcert -install
      - mkcert localhost 127.0.0.1 (localhost.pem, localhost-key.pem 생성)
      - 서버 HTTPS 설정에 적용 (CN/SAN에 localhost, 127.0.0.1 포함)

2. VS Code 열기 -> Command Palette 실행 (⇧⌘P) ->상단 메뉴 → View → Command Palette… (단축키: ⇧⌘P).

3. 검색창에 다음 입력 후 실행하세요 -> Shell Command: Install 'code' command in PATH

4. CA와 함께 실행  -> NODE_EXTRA_CA_CERTS="$(mkcert -CAROOT)/rootCA.pem" code .
