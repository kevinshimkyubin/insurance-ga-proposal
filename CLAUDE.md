# 보험/GA 맞춤 채널톡 제안서 — 템플릿 (Claude Code 가공용)

이 저장소는 **GA(법인보험대리점)별 맞춤 채널톡 세일즈 제안서 템플릿**입니다.
새 GA에 맞게 가공할 때는 이 문서의 규칙을 따르세요.

---

## 🚀 사용법
1. 폴더를 열고 요청: **"이 제안서를 〈GA명〉에 맞게 가공해줘"**
2. 아래 체크리스트대로 수정 → 렌더 검증 → (원하면) 커밋·푸시
3. GitHub Pages 링크로 공유

---

## ⚠️ 반드시 지킬 규칙
1. **수정 후 `index.html` 동기화** — `cp proposal.html index.html` 안 하면 공유 링크에 반영 안 됨.
2. **한글·한자는 raw로 입력** — `\uXXXX` 이스케이프 금지 (손코딩 오타 방지).
3. **톤·구조·색 유지** — 내용만 GA 맞춤으로. 색: 보라=브랜드 / 빨강=문제(before) / 초록=해결(after).
4. **AI 명칭** — 고객 대상 문구는 "AI 에이전트"/"AI(ALF)"로 표기 (내부용어 CoS 지양).

---

## ✅ GA 맞춤 체크리스트
| 바꿀 것 | 찾기 (grep) | 비고 |
|---|---|---|
| **GA 회사명** | `○○ GA` | 1·2·3막 디바이더 인물 소개 (3곳) |
| **담당·연락처** | `담당 ○○○`, `○○○@channel.io` | 마지막 Thank you |
| **ROI 예시값** | ROI 장표 | 규모에 맞게 (전부 예시·가정) |
| (선택) 레퍼런스 | `img/reference.png` | 자사 GA 고객사 로고월로 교체 |
| (선택) 인물명 | `본부장님`, `박현우`, `수민` | 필요 시 이름만 |

---

## 🧩 구조 (톤 유지용)
1. **표지 → 성과 → 레퍼런스 → 제품 소개 → 역할별 문제(3카드)**
2. **1막 경영**(본부장): 개인폰 소통 → 데이터 못 봄 → 채널톡 통합·대시보드·AI 분석
3. **2막 영업**(박현우 FC): 전화로만 영업 → 고객 못 받음 → 채팅 전환·유실콜 회수·AI 에이전트 상담 지원
4. **3막 운영**(수민 매니저): 설계사 반복 문의 폭주 → AI 24시간 자동 응대·매뉴얼 학습·자동 라우팅
5. **정리 → 기능 맵 → 솔루션 통합 → ROI → 도입 로드맵 → 도입 프로세스 → Thank you**

---

## 🔢 슬라이드 추가/삭제 후 — 페이지번호 재계산
```python
import re
s=open("proposal.html").read()
s2=re.sub(r'<div class="pagemark">\d+</div>',
          lambda m: f'<div class="pagemark">{1+s.count(chr(60)+"section",0,m.start())}</div>', s)
open("proposal.html","w").write(s2); open("index.html","w").write(s2)
```

## 📤 커밋·푸시 (온라인 링크 반영)
```bash
cp proposal.html index.html
git add -A && git commit -m "〈GA명〉 맞춤 가공"
git push origin main
```
