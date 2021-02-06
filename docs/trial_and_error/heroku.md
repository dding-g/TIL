## Heroku 배포 후 에러 : code=H14 desc="No web processes running"

- Heroku로 프로젝트를 배포하고 모든 값을 맞춰주었다고 생각 했는데도 위와 같은 오류가 나옴.
- 말 그대로 아무런 Web Process가 동작하고 있지 않은 오류인데, 나는 분명히 `Procfile`에 `web: npm run start` 를 명시해 준 상태였음.
- 원인은 Heroku의 `Dynos`가 꺼져 있는 상태여서 나는 에러였음. `Dynos`가 커스텀으로 실행 가능 한 command들 이라고 보면 될 듯. free는 1개를 제공하는데 내가 아까 테스트 하다가 꺼버리고 다시 안켜놨었음 ㅠ
- Heroku 페이지에서도 켤 수 있지만, `heroku -a APP_NAME ps:scale web=1` 로 켤 수 있음.
- 여담으로 `Procfile`은 프로젝트의 최상단에 와야 한다.

## Heroku 배포 후 에러 : Error R10 (Boot timeout) -> Web process failed to bind to $PORT within 60 seconds of launch

- `npm run start`의 내용이 `next start` 였는데, `next start -p $PORT`로 바꾸어 해결.
- local에서는 그냥 3000으로 열어도 상관 없지만, heroku는 어떤 이유 때문에 포트를 계속 바꾸어 주는듯.

## 설치
- `curl https://cli-assets.heroku.com/install-ubuntu.sh | sh`
- 로그인 : `heroku login`

## 로그
- `heroku logs --tail -a APP_NAME`