# 🚀 Hướng Dẫn Đẩy Code Lên GitHub/GitLab

## Bước 1: Tạo Repository Trên GitHub

### A. Tạo Repo Mới
1. Đăng nhập vào [GitHub.com](https://github.com)
2. Click **"New"** (hoặc **+** icon → **New repository**)
3. **Repository Name:** `GTH-Project-2026`
4. **Description:** `Green Tech Hub - Technology for a Greener Future`
5. **Visibility:** Public (hoặc Private nếu cần)
6. ✅ **Initialize repository** - Có thể chọn thêm .gitignore và LICENSE
7. Click **"Create repository"**

### B. Copy Repository URL
- Copy HTTPS URL (hoặc SSH nếu đã setup SSH keys)
- Ví dụ: `https://github.com/yourusername/GTH-Project-2026.git`

---

## Bước 2: Kết Nối Remote Repository Tại Local

Chạy lệnh sau tại thư mục dự án:

```bash
cd c:\Users\quang\Desktop\green-tech-hub

# Thêm remote (thay URL bằng repository của bạn)
git remote add origin https://github.com/yourusername/GTH-Project-2026.git

# Kiểm tra remote
git remote -v
```

**Output expected:**
```
origin  https://github.com/yourusername/GTH-Project-2026.git (fetch)
origin  https://github.com/yourusername/GTH-Project-2026.git (push)
```

---

## Bước 3: Đẩy Code Lên GitHub

### A. Push Main Branch
```bash
# Đặt tên branch hiện tại thành 'main' (nếu chưa)
git branch -M main

# Push master/main branch
git push -u origin main
```

### B. Push Develop Branch
```bash
# Chuyển sang develop branch
git checkout develop

# Push develop branch
git push -u origin develop
```

### C. Push Feature Branches
```bash
# Push feature/landing-page
git push -u origin feature/landing-page

# Push feature/contact-form
git push -u origin feature/contact-form
```

### D. Kiểm Tra Sau Push
```bash
# Xem tất cả remote branches
git branch -a

# Output:
# main
# develop
# feature/landing-page
# feature/contact-form
# remotes/origin/main
# remotes/origin/develop
# remotes/origin/feature/landing-page
# remotes/origin/feature/contact-form
```

---

## Bước 4: Tạo Pull Request (PR) Trên GitHub

### A. PR từ feature/landing-page vào develop

1. Vào GitHub repository
2. Click **"Pull requests"** tab
3. Click **"New pull request"**
4. **Base:** `develop`
5. **Compare:** `feature/landing-page`
6. **Title:** `GTH-2 & GTH-3: Enhance landing page with navbar and footer`
7. **Description:**
   ```
   ## Changes
   - GTH-2: Improve navbar with navigation menu and sticky positioning
   - GTH-3: Add footer and social media icons
   
   ## Test Result
   - ✅ Navbar sticky on scroll
   - ✅ Navigation links work
   - ✅ Social icons display correctly
   - ✅ Mobile responsive
   
   Relates to: GTH-FRONTEND epic
   ```
8. Click **"Create pull request"**
9. **Review code** đảm bảo mọi thứ ổn định
10. Click **"Merge pull request"** → **"Confirm merge"**
11. Delete branch (nếu cần)

---

### B. PR từ feature/contact-form vào develop

1. Click **"New pull request"**
2. **Base:** `develop`
3. **Compare:** `feature/contact-form`
4. **Title:** `GTH-4: Add contact form for partner inquiries`
5. **Description:**
   ```
   ## Changes
   - Add comprehensive contact form
   - Form validation (name, email, message)
   - Vietnamese character support
   - Success/error message display
   
   ## Test Result
   - ✅ Form validation works
   - ✅ Vietnamese characters accepted
   - ✅ Email validation
   - ✅ Mobile responsive
   
   Relates to: GTH-FRONTEND epic
   ```
6. Merge sau khi approve

---

### C. PR từ develop vào main (Production Release)

1. Click **"New pull request"**
2. **Base:** `main`
3. **Compare:** `develop`
4. **Title:** `Release v1.0.0 - Green Tech Hub Landing Page`
5. **Description:**
   ```
   ## Release Summary
   Initial release of Green Tech Hub Landing Page v1.0.0
   
   ## Features Completed
   - ✅ Hero section with "Technology for a Greener Future" message
   - ✅ Solutions section (Solar Energy, Waste Management, Smart Irrigation)
   - ✅ Contact form with validation
   - ✅ Responsive design for all devices
   - ✅ Footer with social media links
   
   ## Commits
   - GTH-1: Initial project setup
   - GTH-2: Navbar improvements
   - GTH-3: Footer and social icons
   - GTH-4: Contact form
   - GTH-5: Landing page enhancements
   
   ## Quality Assurance
   - ✅ Cross-browser tested
   - ✅ Mobile responsive verified
   - ✅ Form validation working
   - ✅ Performance optimized
   
   Closes: #1, #2, #3, #4, #5
   ```
6. Merge with **"Create a merge commit"** option

---

## Bước 5: Xem Git Log Trên GitHub

1. Vào GitHub repository
2. Click **"Code"** → **"Commits"** để xem commit history
3. Xem branches tại **"Branches"** tab
4. Xem pull requests tại **"Pull requests"** tab

---

## Complete Git Flow Diagram

```
┌─────────────────────────────────────────┐
│   GitHub Repository (Remote)            │
│   GTH-Project-2026                      │
└─────────────┬───────────────────────────┘
              │
              │ git push -u origin main/develop
              │
┌─────────────▼───────────────────────────┐
│   Local Repository                      │
│   green-tech-hub/.git                   │
├─────────────────────────────────────────┤
│  Branches:                              │
│  ✓ main (production)                    │
│  ✓ develop (integration)                │
│  ✓ feature/landing-page                 │
│  ✓ feature/contact-form                 │
└─────────────────────────────────────────┘
```

---

## Lệnh Nhanh Toàn Bộ Quy Trình

```bash
# 1. Kiểm tra status
git status

# 2. Thêm remote
git remote add origin https://github.com/yourusername/GTH-Project-2026.git

# 3. Push tất cả branches
git push -u origin --all

# 4. Kiểm tra remote branches
git branch -r

# 5. Tạo PR trên GitHub web interface
# (Không thể tạo PR từ command line trực tiếp)
```

---

## Troubleshooting

### Error: Remote repository not found
```bash
# Kiểm tra remote URL
git remote -v

# Xóa remote sai và thêm lại
git remote remove origin
git remote add origin https://github.com/yourusername/GTH-Project-2026.git
```

### Error: Failed to push (rejected)
```bash
# Pull changes trước
git pull origin main

# Giải quyết conflict nếu có
# Sau đó push lại
git push origin main
```

### Push từ feature branch
```bash
git checkout feature/landing-page
git push -u origin feature/landing-page
```

---

## Kết Quả Cuối Cùng Trên GitHub

✅ **Repository Structure:**
```
GTH-Project-2026/
├── main branch (production ready)
├── develop branch (integration)
├── feature/landing-page (merged)
└── feature/contact-form (merged)

Pull Requests:
├── #1 - GTH-2 & GTH-3: Enhance landing page ✓ MERGED
├── #2 - GTH-4: Add contact form ✓ MERGED
└── #3 - Release v1.0.0 ✓ MERGED
```

**Commit History:**
```
* Release commit (main)
|\ 
| * GTH-5: Landing page enhancements (develop)
| * GTH-4: Contact form
| * GTH-3: Footer and social icons
| * GTH-2: Navbar improvements
|/
* GTH-1: Initial setup
```

---

## Next Steps

1. ✅ Repository created and code pushed
2. ✅ Branches organized (main, develop, feature/*)
3. ✅ Pull requests reviewed and merged
4. 📝 **Next:** Setup CI/CD pipeline (GitHub Actions)
5. 📝 **Next:** Setup auto-deployment to web server

---

**Date:** March 18, 2026  
**Status:** ✅ Ready for GitHub Deployment  
**Template Version:** 1.0
