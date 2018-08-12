## 11 câu hỏi phỏng vấn hack não về Git sẽ khiến bạn muốn khóc.

Dựa theo việc khảo sát các developer gần đây nhất trên Stack Overflow , có đến hơn 70% developers sử dụng git , Tạo nên làn sóng sử dụng VCS trên thế giới. Git thường được sử dụng  trên việc phát triển mã nguồn mở hay phần mềm thương mại , đem lại nhiều lợi ích đáng kể cho cá nhân , nhóm và các doanh nghiệp.

#### Q1 : Git fork là gì ? Điểm khác biệt giữa fork , branch và clone ?

- Fork là một remote , một bản sao chép phía server từ một repository.Một bản khác sinh ra từ bản gốc . Fork không phải là một khái niệm cụ thể của Git.Nó đơn giản là những ý tưởng về chính trị / xã hôi.
- Clone không phải là fork; clone là một bản copy dưới local của một vài remote repository. Khi bạn clone , bạn thực ra là đang tạo nên bản copy của 1 thực thể repository gốc, bao gồm tất cả về lịch sử và các nhánh.
- Branch  là một cơ chế để xử lý các thay đổi trong một kho lưu trữ duy nhất để cuối cùng hợp nhất chúng với phần còn lại của mã. Branch là một tập con của repository. Về mặt lý thuyết, nó là đại diện cho một luồng phát triển.


#### Q2: Điểm khác biệt giữa một "pull request" và một "branch"?

- Branch chỉ là một phiên bản chia nhỏ từ một bộ code.

- Pull request là khi ai đó tác động đến repository , tạo nhánh riêng , tạo các thay đổi , sau đó cố gắng để hợp nhât vào chính nhánh đó (Đưa những thay đổi vào trong repository của người khác ).

#### Q3: Điểm khác biệt giữa  "git pull" và git fetch"?

Hiểu đơn giản nhất là, git pull thực hiện git fetch sau đó là git merge

Khi bạn sử dụng pull, Giu sẽ tự động thực hiện công việc của bạn thay bạn. Tùy theo từng hoàn cảnh , Git sẽ merge bất kỳ các commit nào vào nhan hs mà bạn đang làm việc.Pull sẽ tự động gộp các commit mà bạn sẽ không cần phải review trước.Nếu bạn không quản lý chặt chẽ nhánh của bạn , bạn sẽ thường xuyên gặp phải conflict.

Khi bạn fetch , Git sẽ tập hợp các commit từ nhánh đang được target không tồn tại trong nhánh của bạn và lưu trữ chúng ở trong local repository , tuy nhiên , nó sẽ không merge chúng với nhánh hiện tại. Điều đó thực sự hữu dụng nếu bạn cần giữ việc cập nhật repository, nhưng việc đó có thể bị ngưng nếu bạn cập nhật file của bạn.Để tích hợp commit vào trong nhánh master , sử dụng merge.

#### Q4: Làm cách nào để quay trở lại lần commit trước trong git ?

Giả sử bạn gặp vấn đề này ,C chính là Head và (F) là trạng thái files của bạn.
Để loại bỏ những thay đổi trong commit:
Bây giờ B chính là Head bởi vì bạn để sử dụng --hard , file của bạn đã reset trạng thái về commit B
để hoàn tác lại commit nhưng giữ lại các thay đổi:

``
git reset HEAD~1
``
Bây gừi chúng ta sẽ bảo Git di chuyển con trỏ Head trở lại commit (B) và để các file giống nhau và các trạng thái git hiển thị các thay đổi đã được check trong C
Để hoàn tác commit nhưng giữ file và index
Khi bạn thực hiện git status, bạn sẽ thấy những file cùng index như nhau trước đấy.

#### Q5: "git cherry-pick" là gì?

The command git cherry-pick is typically used to introduce particular commits from one branch within a repository onto a different branch. A common use is to forward- or back-port commits from a maintenance branch to a development branch.

This is in contrast with other ways such as merge and rebase which normally apply many commits onto another branch.

Consider:

`git cherry-pick <commit-hash>`
