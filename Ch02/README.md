# IN4211 — Ch02: Refactoring EduHub với SOLID và Design Patterns

Điểm xuất phát (starter) của bài tập Chương 2. Dự án **build và chạy được ngay**, nhưng
`ClubManager` cố tình viết sai (God class vi phạm SRP, OCP, DIP). Nhiệm vụ của bạn là refactor.

## Yêu cầu

- [.NET SDK 10.0](https://dotnet.microsoft.com/download)
- Git

## Bắt đầu

```bash
# 1. Fork repo này về tài khoản của bạn, rồi clone
git clone https://github.com/<tài-khoản-của-bạn>/<tên-repo>.git
cd <tên-repo>/Ch02

# 2. Tạo nhánh làm bài
git switch -c feature/solid-refactor

# 3. Kiểm tra mọi thứ chạy được
dotnet build Ch02.Refactor.sln
dotnet test Ch02.Refactor.sln
dotnet run --project Ch02.Refactor
```

Kết quả ban đầu: build thành công, 1 test xanh, 6 test bị `Skip`.

## Cấu trúc

```
Ch02/
├── Ch02.Refactor/              # Project chính
│   ├── ClubManager.cs          # God class cần refactor (đọc TODO 1-5 ở đầu file)
│   ├── Domain/                 # Club, Member, Event (có TODO cần hoàn thiện)
│   └── Program.cs              # Demo chạy code cũ
└── Ch02.Refactor.Tests/        # xUnit
    └── DomainTests.cs          # Test mẫu + 6 test Skip cần viết
```

## Việc cần làm

| # | Nhiệm vụ | Nơi làm |
|---|---|---|
| 1 | Phân tích ≥ 4 vi phạm SOLID (dòng nào, nguyên tắc nào, hậu quả gì) | Nộp theo yêu cầu của đề bài |
| 2 | Tách ≥ 4 class/interface (`ClubService`, `IClubRepository`, `EventService`, `ReportService`, `IAppLogger`, `INotificationService`), phụ thuộc qua constructor | `Ch02.Refactor/` |
| 3 | Áp dụng 4 pattern: Factory, Decorator, Strategy, Observer | `Ch02.Refactor/` |
| 4 | Hoàn thiện `Club.Create`, `Club.HasRoom`, `Event.Register`, `Event.CheckIn`; viết ≥ 6 test AAA | `Domain/`, `Ch02.Refactor.Tests/` |
| 5 | Git workflow: nhánh `feature/solid-refactor`, Conventional Commits, rebase, Pull Request | GitHub |

Tìm nhanh các chỗ cần làm: `grep -rn "TODO" --include=*.cs .`

## Quy ước Git

Commit theo [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(club): extract ClubService from ClubManager
refactor(notify): replace if/else with NotificationServiceFactory
test(domain): add Club.HasRoom boundary tests
docs: update README
```

Trước khi mở PR:

```bash
git fetch origin
git rebase origin/main
dotnet test Ch02.Refactor.sln
git push -u origin feature/solid-refactor
```

Mô tả PR theo mẫu có sẵn (what, why, how to test). CI sẽ tự chạy build + test.

## Đề bài và rubric

Xem `de-bai.html` và `rubric.html` trên LMS của lớp.
