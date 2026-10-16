# Checklist truoc khi nop (xoa file nay khi nop cung duoc)

## 0. Doi ten thu muc: MSSV_HoTen_Lab7 -> vi du 2012345_NguyenVanA_Lab7

## 1. Lenh chay trong thu muc du an
pip install -r requirements.txt

# Log 1
coverage run -m unittest discover -s . -p "test_*.py" > logs/local_test.log 2>&1
coverage report -m >> logs/local_test.log

# Git (thay MSSV + ten that cua em)
git init
git config user.name "MSSV - Ho Va Ten"
git config user.email "mssv@dlu.edu.vn"
git branch -M main
git add . && git commit -m "Initial commit"
git remote add origin <LINK_REPO_GITHUB>
git push -u origin main

# Log 2 (chay sau khi da commit nhieu lan, o Tiet 4)
git log --graph --pretty=format:"%h - %an (%ad): %s" > logs/git_history.log

## 2. Log 3: tai tu GitHub Actions (View raw logs) -> logs/github_actions_run.log

## 3. Viec em phai tu lam
- MinhChung_VietTay_MSSV.pdf: 4 trang viet tay (so do CI, bang test case, 6 cau hoi) co ho ten, MSSV, ngay, chu ky
- BaoCao_KetQua_Lab7.pdf: link GitHub + anh chup Actions (do -> xanh, break the build, artifact)
- Break the Build: them ham sai cu phap vao yummy_app.py, push, thay do, xoa, push lai
- Tiet 3: de dat dung quy trinh "do -> xanh", commit rieng file test_yummy_app.py sau khi
  da push workflow co Quality Gate (luc do coverage ~35% se do)

## 4. Nen zip
zip -r MSSV_HoTen_Lab7.zip MSSV_HoTen_Lab7 -x "*/.git/*" "*/__pycache__/*"
