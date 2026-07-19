# 크리스탈 컬렉션 — APK 빌드

크리스탈 테트리스 + 캔디 매치를 담은 안드로이드 앱입니다.
PC 없이 GitHub Actions만으로 APK를 만들 수 있습니다.

## 빌드 방법 (PC 불필요)

1. GitHub에 새 저장소를 만들고 이 폴더 전체를 올립니다
   (또는 이 zip을 풀어서 올립니다).
2. 저장소의 **Actions** 탭으로 갑니다.
3. **Build APK** 워크플로 → **Run workflow** 를 누릅니다
   (push 하면 자동으로도 돌아갑니다).
4. 빌드가 끝나면 (5~10분) 실행 결과 페이지 하단
   **Artifacts** 에서 `crystal-collection-apk` 를 내려받습니다.
5. 압축을 풀면 `app-debug.apk` 가 나옵니다. 폰에 설치하세요
   (설정에서 "출처를 알 수 없는 앱 설치" 허용 필요).

## 오프라인 동작

빌드 과정에서 Three.js(3D 렌더 라이브러리)를 HTML에 직접 심어넣기 때문에,
설치 후에는 인터넷 없이 완전히 오프라인으로 동작합니다.
저장(레벨·별점·최고 기록)은 앱 내부에 남습니다.

## 게임을 수정하려면

`app/src/main/assets/index.html` 한 파일만 고치면 됩니다.
이게 게임 전체입니다. 고친 뒤 다시 push 하면 새 APK가 나옵니다.

## 폴더 구조

- `app/src/main/assets/index.html` — 게임 본체 (이거 하나가 전부)
- `app/src/main/java/.../MainActivity.java` — WebView로 게임을 띄우는 껍데기
- `app/src/main/AndroidManifest.xml` — 앱 정보
- `.github/workflows/build-apk.yml` — 자동 빌드 설정
