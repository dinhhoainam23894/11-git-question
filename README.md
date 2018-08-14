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

Câu lệnh git cherry-pick thường được sử dụng để giới thiệu các commit cụ thể từ 1 nhánh của một repository đối với một nhánh khác.các commit thường được sử dụng là forward và back-port từ nhánh bảo trì đến nhánh phát triển.

Điều này tương phản với các cách khác như merge và rebase thường thì chấp nhận nhiều commit trên một nhánh khác.

Ví dụ:

`git cherry-pick <commit-hash>`

#### Q6: Giải thích những ưu điểm của cơ chế Forking

Topic: Git
Difficulty: ⭐⭐⭐

Cơ chế Forking về cơ bản là khác hoàn toàn với cơ chế phổ biến khác của Git.Thay vì sử dụng một kho lưu trữ phía máy chủ duy nhất hoạt động như một codebase "trung tâm" , nó cung cấp mọi nhà phát triển  có repository phía máy chủ của riêng họ. Cơ ché Forking thường được thấy trong những dự án mã nguồn mở.

Ưu điểm chính của cơ chế forking là những đóng góp có thể được tích hợp mà không cần mọi người phải đẩy vào repository trung tâm để điều khiển việc xóa lịch sử.Các nhà phát triển đẩy vào những repository phía server của họ , và duy nhất những người bảo trì dự án có thể push vào repository chính thức.

Khi những nhà phát triển chuẩn bị để công bố một commit cục bộ , họ đẩy những commit vào repository riêng không phải là repository chính thức.sau đó họ gửi yêu cầu kéo file repository chính , cho phép người bảo trì dự án biết rằng bản cập nhật đã sẵn sàng để được tích hợp.

#### Q7:Nói cho tôi biết điểm khác biệt giữa Head , working tree  và index trong git ? 
Topic: Git
Difficulty: ⭐⭐⭐
The working tree/working directory/workspace là thư mục cây của (nguồn) các file mà bạn có thể thấy và chỉnh sửa.
The index/staging là các file đơn lẻ , lớn, file nhị phân trong /,git/index , liệt kê tất cả các file ở trong nhánh hiện tại ,  check tổng sha1 , thời gian và tên file - nó không phải là thư mục khác với các bản sao file trong đó.
Head là một tham chiếu đến commit cuối cùng trên check-out nhánh hiện tại.

#### Q8:Bạn hãy giải thích về cơ chế của Gitflow? C
Topic: Git
Difficulty: ⭐⭐⭐

Cơ chế gitflow sửa dụng 2 nhánh long-running song song nhau để ghi lại lịch sử của dự án , master và develop:
Master : thường xuyên sử dụng để  phát hành trên LIVE ,với mọi sự kiểm tra và phê duyệt đầy đủ (production-ready).

Hotfix - nhánh bảo trì hay 'hotfix' được sử dụng trong bản vá production được phát hành nhanh chóng. Nhánh Hotfix rất giống với nhánh release và nhánh feature ngoại trừ việc chúng dựa trên master thay vì develop.

Develop - là nhánh bảo gồm tất cả nhánh feature đã được merge và tất cả các test đã được thực hiện.Khi tất cả mọi vấn để đã được kiểm tra và sửa chữa nó mới có thể được merge vào nhánh master.

Feature - mỗi feature mới thì nên được đặt ở nhánh riêng , có thể được đẩy vào nhánh develop như cha mẹ chúng.

#### Q9: Khi nào bạn nên sử dụng 'git stash' ? 
Topic: Git
Difficulty: ⭐⭐⭐
Câu lệnh git stash lấy tất cả những thay đổi uncommited của bạn (bao gồm cả staged và unstaged) , lưu chúng để sử dụng sau này , và sau đó phục hồi chúng từ bản sao làm việc của bạn.

Ví dụ:
`
$ git status
`
Trên nhánh master
Thay đổi committed:
`
new file: style.css
`
thay đổi not staged từ commit:
`
modified: index.html
$ git stash
`

Lưu thư mục làm việc và index trạng thái WIP trên master:Saved working directory and index state WIP on master: 

`5002d47 our new homepage
HEAD is now at 5002d47 our new homepage
$ git status
On branch master
nothing to commit, working tree clean
`
``
Một nơi chúng ta có thể sử dụng stashing là nếu chúng ta nhận ra rằng chúng ta quên điều gì đó ở lần commit trước và sẵn sàng bắt đầu công việc vào lần kế tiếp trên nhánh đó.

stash những đống lộn xộn mà tôi đã tạo ra
`
$ git stash save
`
Một vài thay đổi ở thư mục làm việc
và bây giờ thêm chúng vào lần commit cuối:
`
$ git add -u
$ git commit --ammend
`
quay trở lại công việc

`
$ git stash pop
`

#### Q10:Làm cách nào để loại bỏ file từ fit mà không phải loại bỏ chúng từ file hệ thống?
Topic: Git
Difficulty: ⭐⭐⭐⭐

Nếu bạn không cẩn thận trong việc dùng git add , bạn sẽ thêm những file mà bạn không hề muốn commit. Tuy nhiên git rm sẽ loại bỏ chung từ cả trong staging (index) , tốt như hệ thống file của bạn (working tree) , có thể không phải thứ bạn thực sự muốn.

Thay vào đó hãy sử dụng git reset : 
`
git reset filename     
`
Hoặc là
`
echo filename >> .gitingore # add it to .gitignore to avoid re-adding it
`
Điều này có nghĩa là git reset <paths> trái ngược với git add <paths>


#### Q11:Khi nào bạn sử dụng "git rebase" thay vì "git merge" ?
Topic: Git
Difficulty: ⭐⭐⭐⭐⭐

Cả 2 câu lệnh trên đều được tạo ra để tích hợp những thay đổi từ một nhánh vào nhánh khác - chúng làm việc đó theo nhiều cách khác nhau.

Xem xét merge/rebase:

A <- B <- C    [master]
^
 \
  D <- E       [branch]

sau khi dùng git merge master:

A <- B <- C
^         ^
 \         \
  D <- E <- F
sau khi dùng rebase master:

A <- B <- C <- D <- E
Với rebase bạn có thể  dùng trên nhánh khác như một base mới cho  công việc của bạn.

Khi bạn sử dụng : 

When to use:

 - Nếu bạn có bất cứ nghi ngờ nào , sử dụng merge.
- Chọn rebase hay merge cơ bản là việc bạn muốn lịch sử của bạn trông như nào thôi. 
Một vài yếu tố để xem thêm:

- Là nhánh bạn đang nhận sự thay đổi  được chia sẻ từ  những nhà phát triển khác bên ngoài team của bạn (ví dụ như mã nguồn mở , public)  Nếu là nó thì đừng sử dụng rebase.Rebase phá hủy nhánh của bạn và những repository nhà phát triển đó thường là bị hỏng / thiếu sự nhất quán trừ khi họ sử dụng 
`
git pull --rebase
`
- Điều gì hủy hoại team phát triển của bạn ? Rebase là  một trong những tác nhân phá hoại. Điều đó có nghĩa là , nếu bạn không duyệt chính xác , bạn có thể mất những  commit công việc của bạn  và/hoặc phá hỏng tính nhất quán của những repository của nhà phát triển khác.

- Bản thân nhánh có đại diện cho thông tin hữu ích không? Một số nhóm sử dụng mô hình  branch-per-feature cho nhánh, trong đó mỗi nhánh đại diện cho một đối tượng hoặc bugfix, hoặc tính năng phụ, vv) Trong mô hình này nhánh giúp xác định các tập hợp các commit liên quan. Trong trường hợp branch-per-developer, chính nhánh không truyền tải bất kỳ thông tin bổ sung nào (commit đã có tác giả). Sẽ không có hại gì khi rebasing.
- Bạn có muốn phục hồi lại merge vì lý do nào đó không ? Reverting ( giống như là undoing) 1 rebase khá là khó khăn và/hoặc không thể (nếu rebase có lỗi xung đột) so sánh với độ phục hồi lại của merge.Thử nghĩ đi nếu có 1 cơ hội bạn sẽ  muốn phục hồi sau khi sử dụng merge.
