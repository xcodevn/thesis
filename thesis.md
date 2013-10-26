INTERACTIVE VERIFICATION AND SPEED UP TECHNIQUES
================================================

- PURPOSE
  + Luan van nay tro thanh kieu mau cho luan van ki su sau nay.
  + Nguoi doc chi can nhung kien thuc co ban ve Khoa hoc may tinh co the doc va hieu hoan toan noi dung cua luan van (mot dang cua self-contains)
  + Ngon ngu don gian, gan gui, de hieu, mot it di dom cua tac gia.
  + An chua giong van rieng cua tac gia, va nhung kinh nghiem co duoc trong qua trinh lam luan van 
  + Chi tiet den muc toi da co the, viec nay se mat nhieu thoi gian nhung ket qua mang lai se rat tuyet voi
  + Nhu mot quyen sach giao khoa thuong thuc!
  + Truyen tai mot luong tri thuc khong lo va thu vi den voi nguoi doc!
  + Lam cho nguoi doc hung thu doc, nhu mot cau chuyen ke li ky va hap dan~
  + Dua nguoi doc toi the gioi tuyet voi cua logic hoc!

Abstract
-------

> Beware of bugs in the above code; I have only proved it correct, not tried it -- Donald Knuth

Chứng minh tính đúng đắn của một chương trình may tinh dung formal methods [^formalmethods]
 mang lai su dam bao cao nhat cho cho nhung chuong trinh yeu cau su chinh xac tuyet
doi (chuong trinh lai tau vu tru, may bay, tau dien ngam, ...).
Tuy nhien day khong phai la mot cong viec de dang, hiện nay chuong trinh máy tính vẫn chưa thể tự động hoàn
toàn trong việc chứng minh các chương trình phức tạp trong thuc te [cite-source].
 Mot he qua la phải có sự tương tác giữa người với máy tinh trong quá
trình chứng minh cac chuong trinh phuc tap.

Luận văn này hiện thực ý tưởng về *interactive verification*, là sự tương tác
giữa người và chương trình chứng minh nhằm chứng minh tính đúng đắn của các
chương trình phức tạp.

> Với việc sử dụng *rewriting term*, hệ thống Leon [footnote] đã có thể tạo ra sự tương tác
hai chiều với người dùng.

Bên cạnh đó, luận văn còn đề cập tới khía cạnh tốc độ của quá trình chứng minh, 
một loạt các kỹ thuật tăng tốc đã được áp dụng nhằm cải tiến tốc độ của hệ thống.
Có thể kể đến ba nổ lực chính: 
(1) áp dụng bộ lọc sử dụng tri thức của hệ thống và học máy để lọc bỏ những
phần thừa trong quá trình tính toán, 
(2) kĩ thuật profiling được áp dụng nhằm phát hiện những mắc xích chiếm lượng
lớn thời gian tính toán, từ đó mà tập trung cải thiện tốc độ của các phần này,
(3) thực hiện song song hóa quá trình chứng minh.

Dựa vào những kĩ thuật trên, luận văn đã đạt được một sự cải thiện rõ rệt về tốc
độ của hệ thống, tốc độ chứng minh đã tăng xấp xĩ **30 lần** so với bản hiện
thực ban đầu.

Bên cạnh những kết quả đạt được trên, bản thân tác giả cũng gặt hái được nhiều
kinh nghiệm quý báu trong quá trình làm luận văn, nhất là kinh nghiệm trong quy
trình hiện thực hệ thống và trong việc đảm bảo chất lượng, tính ổn định của hệ
thống.
Thiet nghi day la nhung kinh nghiem quan trong nhat cho mot nguoi ki su.

-------------------

Acknowledgement
--------------

Tác giả gửi lời cảm ơn chân thành đến phó giáo sư tiến sĩ Quản Thành Thơ, phó
giáo sư tiến sĩ Viktor Kuncak đã có những góp ý quan trọng và định hướng cho
luận văn này.

Tác giả gửi lời cảm ơn của mình đến anh Hoàng Lê Nghĩa Đức, là người đã theo
sát, và hỗ trợ tác giả trong thời gian làm luận văn.

Và trên tất cả, luận văn này dành cho gia đình của tác giả, nhất là người mẹ đã luôn
chăm sóc và dõi theo tác giả.

Gửi lời tưởng nhớ đến thầy Dương Công Vinh, người đã dắt tác giả đi những bước đi
dau tien trên con đường đến với ngành *khoa học máy tính*.

-------------------

Đóng góp của luận văn
--------------------

Luận văn đã mở rộng khả năng của hệ thống hiện tại, cho phép hỗ trợ
chứng minh tương tác, sử dụng các bổ để, từ đó cho phép chứng minh tự động
những tính chất mà trước kia phải dựa vào người sử dụng.

Luận văn cũng nên lên ý tưởng về *interactive learning*, trong đó cho phép giải
thuật học máy có thể học từ chính quá trình sử dụng hệ thống của người dùng.

Với những nổ lực trong việc cải thiện tốc độ, hệ thống đã có những cải
thiện rõ rệt về tốc độ, góp phần cải thiện đáng kể thời gian tương tác với người
dùng. [lủng củng]

Việc sử dụng bộ lọc áp dụng học máy không chỉ có tác dụng tăng tốc cho rieng hệ
thống, mà bộ lọc còn có thể được sử dụng trong các trường hợp tương tự.
Ví dụ như bo loc dam nham vai tro tien xu ly cho de tai tien si "Name it please"

Mot dong gop nho va thuan tuy ve ky thuat, trong thoi gian lam viec voi he thong
Leon tác giả đã phat hien va sửa được một lỗi tồn tại trong một thời gian dài
bên trong nhân của hệ thống.
 
Bên cạnh đó, trong thời gian rãnh rỗi của mình, tác giả cũng đã thiết kế một
giao diện mới cho hệ thống trên nền web.
Tuy khối lượng công việc nhỏ, nhưng cũng coi day là một thói quen có ích trong
thời gian rãnh rỗi.

--------------------------

Table of contain
----------------

Introduction
------------

Logic hoc la linh vuc nghien cuu ve viec suy luan mot cach dung dan, la tru cot
cua toan hoc hien dai. Logic da duoc nha hien triet co dai Aristost nghien cuu
va dat nhung thanh tuu ban dau, co the ke den logic tam doan luan [footnote] cua
ong. 
Logic hoc chi thuc su tro thanh nen tang cua toan hoc tu cuoi the
ky XIX dau the ky XX voi no luc thong nhat nen tang logic cua toan hoc cua
chuong trinh Hilbert[^HG], sau do la su xuat hien cua hai dinh ly bat bao toan cua
Godel, chinh hai dinh ly nay da pha vo chuong trinh Hilbert! Tat nhien khong the vi
ly do khong co mot logic chung nhat cho toan bo toan hoc ma co the choi tu vai
tro nen tang cua logic trong moi linh vuc toan hoc. Voi anh sang soi duong cua
logic hoc, nhung dinh ly toan hoc se luon la nhung chan ly truong ton cung thoi
gian.


Nam 1969, Dana S. Scott[^dana] viet mot bai bao danh dau su ra doi cua *Logic of Computable Functions* - LCF , 
mo ra mot nganh nghien cuu ket hop giua logic hoc va
lambda-caculus, tu do cho ra doi cua ngon ngu lam trinh ham dau tien - ML, ngon ngu co suc anh huong
lon toi nhung ngon ngu lap trinh ham hien dai nhu Ocaml, Haskell, hay Scala. 
Dieu thu vi cua lich su la bai bao nay chua tung duoc cong bo rong rai den tan
nam 1993 vi ly do tac cua bai bao nhan thay su khong can thiet phai xuat ban no.
Co le day la bai bao khong duoc xuat ban co anh huong nhat trong lich su cua
nganh khoa hoc may tinh.

Voi LCF, nhung *proof asisstance*[^proofasiss] da co the chung minh (duoi su tuong tac voi
nguoi dung)
nhung dinh ly lon cua toan hoc, nhu dinh ly bat bao toan cua Godel, dinh ly cuoi
cung cua Fermat[^fermat].
Ben canh do la nhung ung dung thuc tien, cac *proof asisstance* da duoc su dung
de chinh minh tinh dung dang cua phan cung may tinh [cite], cua mot he dieu hanh
hoan chinh [cite L4OS], trinh bien dich [cite], CardJava[cite]

Leon là một chương trình chứng minh tự động được phát triển bởi nhóm nghiên cứu
LARA tại đại học EPFL, Thụy Sĩ.
Điểm mạnh của Leon là cho phép người lập trình dùng chính ngôn ngữ Scala cho
việc đặc tả những tính chất của chương trình Scala.
Leon có thể phát hiện ra các *phản ví dụ* trong trường hợp có sự sai khác giữa đặc
tả và hiện thực.

Về nguyên tắc, Leon thực hiện việc chứng minh trên môt ngôn ngữ gọi là PureScala.
Ngôn ngữ này la mot tap con cua Scala, chỉ hỗ trợ các hàm không có hiệu ứng lề
(thuần hàm) voi yêu cầu các hàm này phải là hàm bậc nhất (không nhận một hàm khác
như là tham số, cũng như không trả về một hàm) và chỉ hỗ trợ các kiểu dữ liệu
đơn giản (số nguyên, kiểu dữ liệu trừu tượng, tập hợp, tuples)

Leon hoạt động dựa trên ý tưởng đơn giản là Unrolling. Để chứng minh một
biểu thức thỏa một tính chất nào đó, với những hàm không đệ quy trong biểu thức,
ta có thể thực hiện đơn giản bởi việc thay lời gọi hàm bằng thân của hàm này đã
được thay các biến bởi các tham số truyền theo. 
Đối với các hàm gọi chính nó (hàm đệ quy) Leon cũng thực hiện tương tự, nhưng
kết quả cho mỗi lần *Unrolling*, ta chỉ được một phiên bản xấp xỉ với hàm đệ qui.
Dựa vào việc *Xấp xĩ cận dưới* (một xấp xĩ mà nếu hàm này trả về là sai với đặc tả
thì hàm đệ quy cũng sai với đặc tả), và *Xấp xĩ cận trên* (một xấp xĩ mà nếu hàm
này trả về là đúng với đặc tả thì hàm đệ quy cũng đúng với đặc tả) ta có thể
thoát ra khỏi quá trình Unrolling vô tận và vẫn đảm bảo tính đúng đắn của chứng
minh (hoặc phản ví dụ). 
Nói một cách ngắn gọn , de chứng minh một tính chất của một biểu thức ta thực
hiện chứng minh trên các xấp xĩ trên và xấp xĩ dưới của biểu thức này.

Tuy nhiên, hệ thống Leon hiện tại hỗ trợ rất kém trong việc chứng minh một tính
chất của chương trình bằng cách sử dụng các bổ đề kèm theo.
Một sự thật rằng đa phần các chứng minh luôn cần những bồ đề kèm theo. 
Có thể giải thích duoc việc này nếu coi Leon là một hệ thống chứng minh diễn dịch,
nói cách khác, thông thường Leon sẽ không thể thực hiện việc chứng minh qui nạp
nếu không có sử tương tác với người dùng..
Chính các bổ đề sẽ lấp đầy mắc xích trống, các bổ đề sẽ nhận nhiệm vụ chứng minh
qui nạp.

Luận văn đưa ra ý tưởng sử dụng rewriting term, để don gian hoa biểu thức cần
chứng minh trước khi đưa cho solver bên dưới.

Quá trình *simplify* một biểu thức là quá trình biển đổi biểu thức về một dạng
tương tương nhưng đơn giản hơn thong qua cac *rewriting rules*.
Bằng việc sử dụng các *rewriting rules* có dạng `if COND then LHS = RHS` ta có
thể thay vế trái `LHS` bằng vế phải `RHS` nếu `COND` được thỏa.
Quá trình xem ra đơn giản này là một trong những cấu thành chính va phuc tap
nhat của các *Interactive proof assistance.*

Bằng việc chuyển đổi các bổ đề, định nghĩa hàm, giả thuyết quy nạp trở thành các
*rewriting rules* ta có thể chứng minh một cách tự động những tính chất mà trước
kia phải làm hoàn toàn bằng tay.

Một trong những chú trọng của luận văn này là cải thiện thời gian chứng minh của
Leon tới mới tối đa có thể. Có thể kể đến ba nỗ lực chính để đạt mục tiêu trên.

Thứ nhất là việc sử dụng một bộ lọc nhằm lọc ra các *rewrite rules* không cần
thiết cho quá trình chứng minh.
Thực nghiệm cho thấy một số lượng rất ít các rules là cần thiết cho quá trình
chứng minh.
Để cải thiện tốc độ ta mong muốn lọc ra nhưng rules cần thiết và loại bỏ những
rules thừa.
Tất nhiên là hiệu năng mang lại phải lớn hơn phí tổn trong khi bộ lọc hoạt động.
Bằng việc sử dụng thuật toán học máy Naive-Bayes, luận văn này hiện thực một bộ
lọc có khả năng học được những tri thức từ quá trình chứng minh trước đó, hoặc
những tri thức do người dùng đưa vào để cải thiện chất lượng của bộ lọc.

Thứ hai là việc sử dụng kĩ thuật profiling, đây là một quy trình kép kín,
profiling cho phép phát hiện những bộ phận trong hệ thống chiếm phần lớn tài
nguyên máy tính (CPU hay RAM) từ đó chúng ta tập trung cải tiến những phần quan
trọng này.
Quy trình này được lập lại, và mỗi lần lặp tốc độ của hệ thống lại được cải thiện.

Nỗ lực thứ ba để đẩy tốc độ của hệ thống và có lẽ là nhân tố quan trọng nhất đó
là thực hiện song song hóa hệ thống hiện tại.
Ý tưởng đơn giản là ta có thể chứng minh các tính chất của chương trình một cách
song song, độc lập với nhau.
Chỉ với nỗ lực này, kết quả đạt được là hệ thống có thể mở rộng tới mức tối đa.

Ở phần cuối của luận văn, tác giả cũng đề cập tới qui trình hiện thực toàn bộ
luận văn sử dụng công cụ quản lý dự án Github cũng như git cho chức năng quản lý
mã nguồn, mà theo ý tưởng của tác giả là điều này nằm ngoài những kiến thức đã
được dạy ở giảng đường.
Bên cạnh đó là kinh nghiệm của tác giả trong việc đảm bảo chất lượng cũng như
tính ổn định của hệ thống thông qua việc thực hiện Regression testing và Tích
hợp liên tục (CI - english please!)

Phần tiếp theo sẽ đi vào chi tiết về interactive verification, các kĩ thuật tăng
tốc được áp dung.


Interactive verification
------------------------

Advanced speed up techniques
-----------------------------

Experiment and Measurement
-------------------------

Conclusion
----------

References
----------

Appendix A - How did I work
----------------------------

Appendix B - Regression test and Continuous integration
--------------------------------------------------------

Appendix C - Leon system
-------------------------

Appendix D - Screen shots
-------------------------


[formalmethods]: de dam bao chuong trinh may tinh lam viec hoan toan dung so voi dac ta cua no ta khong the su dung phuong phep testing truyen thong - http://c2.com/cgi/wiki?TestsCantProveTheAbsenceOfBugs
[dana]: Nguoi dat giai Turing cho nhung dong gop ve Automata theory
[fermat]: dinh ly duoc chung minh boi nha toan hoc ~ten trong khoang thoi gian 10 nam lam viec doc lap
[proofasiss]: la nhung chuong trinh may tinh ho tro nguoi dung trong chung minh
[HG]: Hilbert va Godel duoc coi la 2 trong 4 nha logic vi dai nhat tung song
