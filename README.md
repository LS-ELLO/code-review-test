<img src="https://blog.kshgroup.kr/content/images/2020/04/review.png">

## TODO
- `review-target`은 빈 브랜치로 생성
- rebase를 이용해서 `review`브랜치와 `review-target`브랜치를 병합(not merge)

## 1) 코드리뷰 브랜치 아키텍쳐 자동화
https://blog.kshgroup.kr/code-reviews-for-existing-code-with-github/

## 2) 커밋 시, 리뷰 브랜치를 자동으로 생성 후 lint 적용 점수 도출
- `main(master)`브랜치로의 push는 ignore

## 3) lint점수 이슈탭 업로드 또는 txt파일 도출
- 모든.py파일에 대해(`정규식`) pylint 점수 도출
- artifacts upload: txt파일 다운로드 가능
