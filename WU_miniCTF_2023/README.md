# MiniCTF_2023

## Overview

| Title 	| Category  	| Flag 	|
|-------	|-----------	|------	|
| [Comment](#Comment)  	| Forensics 	| `miniCTF{ch3ck_c0mm3nt}`   	|
| [Notepad](#Notepad)  	| Forensics 	| `miniCTF{f1nd_m3_1n_th3_ch405}`   	|
| [Redacted](#Redacted)  	| Forensics 	| `miniCTF{r3d4ct3d_m3ss4g3_15nt_h4rd_r1ght}`   	|
| [What's_wrong_with_the_picture](#What's_wrong_with_the_picture)  	| Forensics 	| `miniCTF{nemu_nemu_nyanko}`   	|
| [8bitsound](#8bitsound)  	| Forensics 	| `miniCTF{sp3ctrogr4m_c0lorfu1}`   	|
| [Tired_Cat](#Tired_Cat)  	| Forensics 	| `miniCTF{1m_s0_m0th3r_f^ck1n9_7ir3d_4ll_7h3_7im3}`   	|
| [Sharp_eyes](#Sharp_eyes)  	| Forensics 	| `miniCTF{1_w3nt_crAaazy_0v3r_U}`   	|
| [Ping](#Ping)  	| Misc      	| `miniCTF{64.227.14.145}`   	|
| [NASA](#NASA)  	| Misc      	| `miniCTF{today@nasa.gov}`   	|
| [Caesar_Cipher](#Caesar_Cipher)  	| Warm-up   	| `miniCTF{N0w_U_Kn0w_HoW_t0_3ncrYpt_Ur_M3s54g3}`   	|
| [Binary](#Binary)  	| Warm-up   	| `miniCTF{congratulations}`   	|
| [Base64](#Base64)  	| Warm-up   	| `miniCTF{b4s364_3ncrypt3d_by_ckjd0k}`   	|
| [INT](#INT)  	| Warm-up   	| `miniCTF{5urpr1se_y0u_4re_4maz1n9!!!}`   	|
| [FileFolder](#FileFolder)  	| Warm-up   	| `miniCTF{f0ld3r_w4s_hjdd3n_6y_ckjd0k}`   	|

## Forensics

### Comment

#### Solution

- Ta nhận được 1 bức ảnh. Dựa vào đề bài, flag ta cần tìm sẽ nằm tại phần comment của bức ảnh.

![Alt text](image/image.png)

**Flag**: `miniCTF{ch3ck_c0mm3nt}`.

### Notepad

#### Solution

- Ta nhận được 1 bức ảnh. Dựa vào tên đề bài, ta sẽ mở Notepad để tìm flag. Flag sẽ nằm ở cuối file.

![Alt text](image/image-1.png)

**Flag**: `miniCTF{f1nd_m3_1n_th3_ch405}`.

### Redacted

#### Solution

- Ta nhận được 1 file word có nội dung bị bôi đen.

![Alt text](image/image-2.png)

- Ta chỉ cần copy những phần bôi đen đó, ghép chúng lại và ta sẽ ra được flag.
    - Phần 1: miniCTF{
    - Phần 2: r3d4ct3d_
    - Phần 3: m3ss4g3
    - Phần 4: 15nt_h4rd_
    - Phần 5: r1ght}

**Flag**: `miniCTF{r3d4ct3d_m3ss4g3_15nt_h4rd_r1ght}`.

### What's_wrong_with_the_picture

#### Solution

- Ta nhận được 1 bức ảnh, nhưng khi mở ra thì bị báo lỗi “It looks like we don’t support this file format”.

![Alt text](image/image-3.png)

- Ta sẽ dùng HxD để sửa file signature của bức ảnh. File signature là dữ liệu để nhận diện hoặc xác minh nội dung bên trong file đó và thường được viết dưới dạng hex.

![Alt text](image/image-4.png)

- Ở đây, ta có file đuôi .jpg, nên ta sẽ cần chỉnh sửa lại file signature của nó sao cho phần Decoded text (chính là nội dung ta đọc được nếu mở bằng Notepad) xuất hiện JFIF, tức định dạng file của bức ảnh. Ta sẽ sửa FF D7 FF E1 00 10 4B 46 49 47 sang FF D8 FF E0 00 10 4A 46 49 46 00 01:

![Alt text](image/image-5.png)

- Lưu lại và mở lại bức ảnh, ta sẽ thu được flag.

![Alt text](image/image-6.png)

**Flag**: `miniCTF{nemu_nemu_nyanko}`

### 8bitsound

#### Solution

- Ta nhận được 1 file âm thanh. Ta sẽ mở nó bằng Audacity, một phần mềm dùng để chỉnh sửa âm thanh.

![Alt text](image/image-7.png)

- Ta sẽ chuyển từ dạng Waveform sang dạng Spectrogram.

![Alt text](image/image-8.png)

- Spectrogram là một cách biểu diễn trực quan các tần số của một tín hiệu nhất định với thời gian. Và ta sẽ nhận được flag.

![Alt text](image/image-9.png)

**Flag**: `miniCTF{sp3ctrogr4m_c0lorfu1}`.

### Tired_Cat 

#### Solution

Đề bài cho một bức ảnh.
- Ta tải ảnh về và mở ảnh bằng bằng Notepad, lướt đến cuối ta thấy có một link:

![Alt text](image/image-10.png)

- Search link ta thấy link là một tool để giải challange: image/image Steganography

![Alt text](image/image-11.png)

- Vào phần Unhide image/image để giải mã

![Alt text](image/image-12.png)

**Flag**: `miniCTF{1m_s0_m0th3r_f^ck1n9_7ir3d_4ll_7h3_7im3}`.

### Sharp eyes

#### Solution

- Để bài có nói đến sự tinh mắt + xem video ta thấy có nhiều phần của
flag trong đó.
- Có nhiều cách để làm bài này:
    - Chỉnh tốc độ video xuống để nhìn từng ảnh, tuy nhiên cách này hơi mệt vì phải tìm đúng ánh chứa flag, nếu không cẩn thận có thể nhầm lẫn do flag có cả chữ hoa chữ thường.
    - Sử dụng các tool để cắt ảnh từ video. Ở đây ta dùng tool:
https://ezgif.com/video-to-jpg

![Alt text](image/image-13.png)

- Ghép các chữ cái với nhau ta được flag.

**Flag**: `miniCTF{1_w3nt_crAaazy_0v3r_U}`.

### Encyclopedia

- Ta để ý một số chi tiết từ đề bài:
    - Wikipedia bản Eng.
    - IP: 42.113.170.207 . Chú ý đây là IP người dùng chứ không phải
    IP của trang web nào đó.
    - Thêm thông tin lên Wiki.
- Tìm hiểu cách thêm thông tin trên wiki ta nhận được hướng dẫn đó là:
Nhấn vào dấu ba chấm ở góc màn hình bên phải, chọn phần *contributions*

![Alt text](image/image-14.png)

- Điền IP mà đề bài cấp rồi search

![Alt text](image/image-15.png)

- Ta thấy có một số phần được sửa trong một bài viết. Để thấy phần đã sửa chọn vào *diff*

![Alt text](image/image-16.png)

- Ta tìm được thông tin mà người dùng `42.113.170.207` đã sửa.

**Flag**: `miniCTF{Th3_W0rld_1s_so0o_B!9_}`.

## Misc

### Ping

#### Solution

- Đề bài yêu cầu tìm địa chỉ IP của trang web `minictf.infosecptit.club`. Ban đầu, khi
tên miền trang web vẫn còn, chúng ta chỉ cần sử dụng lệnh trong terminal của
máy tính có thể biết được địa chỉ IP của trang web.

![Alt text](image/image-17.png)

- Trong hình trên, tên miền không còn nên chúng ta phải ping thẳng đến IP của
trang web. Và IP này cũng chính là flag của challenge trên.

**Flag**: `miniCTF{64.227.14.145}`.

### NASA

#### Solution

- Từ đề bài ta chú ý đến những chi tiết sau:
    - Tổ chức NASA có trang web là nasa.gov
    - Tài khoản email vào ngày 11 tháng 7 năm 1997
    - Giáo sư Closeheimer, Kahle, Gilliat là ai? Giáo sư Closeheimer chắc là tên của nhân vật trong cốt truyện. Còn khi tôi search “Kahle và Gilliat” thì có một tin rất hữu ích:

![Alt text](image/image-18.png)

- Vào wiki:

![Alt text](image/image-19.png)

- Như vậy ta biết muốn tìm thông tin của web nasa.gov vào ngày 11 tháng 7 năm 1997 thì ta dùng 1 web khác đó là wayback machine. Vào trang web trên nhập URL mà đề bài đã cho:

![Alt text](image/image-20.png)

- Đến đây ta có thể tự dò email hoặc Ctrl + F kí tự @ để tìm email.

**Flag**: `miniCTF{today@nasa.gov}`.

## Warm-up

### Caesar_Cipher

#### Solution 

- Đề cho 1 file cipher.txt chứa đoạn văn bản trông khá giống dạng của flag:
`rnsnHYK{S0b_Z_Ps0b_MtB_y0_3shwDuy_Zw_R3x54l3}`
- Tên đề bài là Caesar Cipher cũng là tên của 1 phương thức mã hóa. Copy đoạn văn
bản đó rồi dán vào tool giải mã Caesar rồi ấn Decrypt ta thấy flag ngay kết quả đầu
tiên

![Alt text](image/image-21.png)

**Flag**: `miniCTF{N0w_U_Kn0w_HoW_t0_3ncrYpt_Ur_M3s54g3}`.

### Binary

#### Solution

- Bài cho chúng ta 1 file binary.txt có nội dung như sau: 01100011 01101111 01101110 01100111 01110010 01100001 01110100 01110101 01101100 01100001 01110100 01101001 01101111 01101110 01110011
- Sử dụng tool chuyển đổi mã nhị phân sang kí tự ta được đoạn văn bản bên trong
flag.

![Alt text](image/image-22.png)

- Sau đó ghép với form flag miniCTF{} ta có flag của bài

**Flag**: `miniCTF{congratulations}`.

### Base64

#### Solution

- File output.txt: `bWluaUNURntiNHMzNjRfM25jcnlwdDNkX2J5X2NramQwa30=`

- Đề bài gợi ý là Base64 => dùng tool encode Base64 ra được flag:

**Flag**: `miniCTF{b4s364_3ncrypt3d_by_ckjd0k}`.

### INT

#### Solution

- Đề bài cho tải về 1 bức ảnh:

![Alt text](image/image-23.png)

- Nhìn qua bức ảnh thì không thấy gì, tên file có vẻ có gì đó đặc biệt, thử tìm phương thức mã hóa tại [link](https://www.dcode.fr/cipher-identifier) (dcode.fr)

![Alt text](image/image-24.png)

- Dùng thử các công cụ https://kt.gy/ thì may mắn ra được flag:

**Flag**: `miniCTF{5urpr1se_y0u_4re_4maz1n9!!!}`.

### FileFolder

#### Solution

- Đề bài cho một file `.rar`, tải về và giải nén thấy khá nhiều folder, lướt xem qua thì thấy có 1 vài folder chứa flag
- Thử sắp xếp lại các folder ở cột date modified:

![Alt text](image/image-25.png)

- Ta nhận được đầu và cuối của flag là: miniCTF{XXXXXXXXX-6y_ckjd0k}
- Đoán được các folder nằm giữa có thể cũng được sửa đi như thế, tìm tương tự với các
folder Me_300, Me_39, Me_495, ....
- Trong folder Me_300 tìm thêm được đoạn: *hjdd3n_6y*
- Trong folder Me_39 tìm thêm được đoạn: *F{f0ld3r*
- Lướt qua các folder sau ta k thấy mảnh flag nào nên quyết định ghép flag rồi submit:
`miniCTF{f0ld3rhjdd3n_6y_ckjd0k}`.
- Flag bị sai, nghĩa là còn thiếu mảnh nào đó, nhìn các mảnh ta thấy được mảnh này nối
với mảnh kia qua 2 kí tự, thử find với 3r.

![Alt text](image/image-26.png)

- Oh sai vài phút ngồi chơi thì ta tìm được mảnh còn sót lại của flag là 3r_w4s_hj

**Flag**: `miniCTF{f0ld3r_w4s_hjdd3n_6y_ckjd0k}`.











