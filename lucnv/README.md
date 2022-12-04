![git-flow](https://raw.githubusercontent.com/tatoanhn02/Git-flow/main/lucnv/gitflow.png)

## Gitflow này dành cho kiểu dự án đặc biệt như KH ĐẤT XANH. Ở đó sẽ release các tính năng riêng sau khi hoàn thành mà không cần phải done tất cả các tính năng đã chọn trong srpint.
### Ý nghĩa của các nhánh

- Nhánh master là nhánh chính để lưu trữ code trên prod.
- Nhánh release là nhánh để test release (round 2)- chỉ khi test done ở nhánh này thì mới merge code lên prod.
- Nhánh develop- chính là nhánh để test round 1
## Ghi chú:
Code sẽ được sync lần lượt từ Master → Release → Develop chỉ được phép sync xuôi từ Master xuống các môi trường khác. Không được sync ngược lại
## Đầu mỗi sprint sẽ tách [tag](https://www.youtube.com/watch?v=2B4Gy-yJmuY) tương ứng với sprint đó từ Master và đặt tên theo sprint.
### 1. Hotfix
Khi có issue trên prod thì sẽ tách nhánh từ Master và đặt tên theo format <b><a href="#branch-formats">{mã_tag_theo_print}/hoxfix/{mã-ticket}</a></b> khi fix xong sẽ merge thẳng vào develop để test round 1, khi done round 1 ở develop sẽ tao MR lên release để test round 2. Khi pass cả 2 round thì sẽ tạo MR từ <b><a href="#ý-nghĩa-của-các-nhánh">release</a></b> lên <b><a href="#ý-nghĩa-của-các-nhánh">master</a></b>.
### 2. Release:
Là nhánh để test pre-prod (round 2). Nên chỉ để build code, không tách nhánh ra từ đây.
### 3. Develop
Là nhánh để test round 1. Nhánh này cũng chỉ để merge và build code. Không tánh nhánh mới từ đây
### 4. Feature
Khi có 1 tính năng mới thì sẽ tách nhánh từ Tag ở Ghi chú và đặt tên theo format <b><a href="#branch-formats">{mã_tag_theo_print}/feature/{mã-ticket}</a></b>. Khi dev xong thì sẽ tạo MR vào <b><a href="#ý-nghĩa-của-các-nhánh">develop</a></b> để verify round 1.
Khi pass round 1 sẽ tạo MR từ feature lên <b><a href="#ý-nghĩa-của-các-nhánh">Release</a></b> để test round 2.

Khi pass round 2 sẽ tạo MR từ feature lên Master để deploy prod.

#### → Tất cả các feature đều làm như vậy.
#### → Tất cả các nhánh ở mục #2, 3, 4. Muốn merge code vào thì phải tạo MR. Không được code trực tiếp trên nhánh đó.

### Cách fix conflict khi merge code vào <b><a href="#ý-nghĩa-của-các-nhánh">Develop</a></b> và <b><a href="#ý-nghĩa-của-các-nhánh">Release</a></b>.
### Develop
Tạo 1 branch mới từ <b><a href="#ý-nghĩa-của-các-nhánh">Develop</a></b> theo format <b><a href="#branch-formats">{mã tag - theo print}/feature_dev/{mã-ticket}</a></b>. Rồi merge branch feature tương ứng vào nhánh mới này để fix conflict. Sau khi fix xong sẽ tạo MR từ nhánh này vào nhánh develop (tương ứng với <a href="#">#F-D1</a> trong hình trên).
### Release
Tương tự như làm với  <b><a href="#develop">Develop</a></b> nhưng khi tách branch mới từ tách từ <b><a href="#ý-nghĩa-của-các-nhánh">Release</a></b> theo cú pháp format <b><a href="#branch-formats"> {mã tag - theo print}/feature_release/{mã-ticket}</a></b> (tương ứng với <a href="#">#F-R</a> trong hình trên).

### Master
Khi tính năng đã pass ở Release thì sẽ tạo MR từ Release lên Master. Những tính năng nào chưa pass thì cần rollback để tránh tình trạng mang hết code mà chưa được verify lên prod.
