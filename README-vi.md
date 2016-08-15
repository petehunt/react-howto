# react-howto

Nếu bạn mới làm quen với React (hoặc phần front-end nói chung) thì bạn sẽ thấy hệ sinh thái tương đối khó hiểu. Có một vài lí do giải thích cho việc đó.

* Trước đây, React mục tiêu hướng tới nhóm đối tượng tiếp cận sớm và các chuyên gia
* Facebook chỉ thực hiện chuyển thành mã nguồn mở khi mà React được thực tế sử dụng, do đó mà không có sự quan tâm vào việc phát triển công cụ cho các dự án nhỏ hơn Facebook.
* Có quá nhiều marketing ảo giả tạo dưới dạng các hướng dẫn về React.

Trong suốt tài liệu này, tôi sẽ giả sử là bạn đã từng có kinh nghiệm xây dựng web với HTML, CSS và Javascript.

## Tại sao bạn nên nghe theo tôi?

Có hàng tấn lời khuyên mâu thuẫn về React bên ngoài; vậy tại sao phải nghe theo tôi nhỉ?

Tôi là một trong những thành viên đầu tiên của nhóm Facebook tham gia xây dựng và triển khai mã nguồn mở thư viện React này. Thêm cả, vì tôi không còn làm ở Facebook nữa, nên tôi có được cái nhìn khách quan không phụ thuộc Facebook nữa.

## Làm thế nào để tương tác với hệ sinh thái của React

Tất cả các phần mềm đều được xây dựng dựa trên một tập hợp các nền tảng công nghệ, và bạn cần phải hiểu rõ về chúng đủ để xây dựng ứng dụng. Nguyên nhân khiến cho công cụ trong hệ sinh thái của React trở nên phức tạp là vì luôn bị giải thích sai thứ tự.

Bạn nền học, theo thứ tự này, **không cần bỏ qua phía trước hoặc học đồng thời**:

* [Thư viện React](#tìm-hiểu-về-react)
* [`npm`](#tìm-hiểu-về-npm)
* [JavaScript “bundlers”](#tìm-hiểu-về-các-công-cụ-đóng-gói-javascript)
* [ES6](#tìm-hiểu-về-es6)
* [Routing](#tìm-hiểu-về-routing)
* [Flux](#tìm-hiểu-về-flux)

**Bạn không cần phải học tất cả những thứ này để có thể làm việc hiệu quả với React.** Chỉ nên chuyển sang bước tiếp theo nếu như bạn thấy có vấn đề cần được giải quyết.

Thêm nữa, có vài chủ đề thường được nhắc đến trong cộng đồng React mà khá "nóng hổi". Những chủ đề dưới đây khá là thú vị nhưng khó để có thể hiểu được và ít phổ biến hơn so với các chủ đề trên và **không cần thiết khi xây dựng ứng dụng**.

* [Inline styles](#tìm-hiểu-về-inline-styles)
* [Server rendering](#tìm-hiểu-về-server-rendering)
* [Immutable.js](#tìm-hiểu-về-immutablejs)
* [Relay, Falcor, etc](#tìm-hiểu-về-relay-falcor-etc)

## Tìm hiểu về React

Có một điều hay bị hiểu nhầm đó là bạn sẽ phí phạm nhiều thời gian trong việc thiết lập công cụ để bắt đầu học React. Trong tài liệu chính thống bạn sẽ thấy [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) là bạn chỉ cần lưu lại một file định dang `.html` và có thể bắt đầu ngay được. **Không cần bất cứ công cụ nào ở bước này, và đừng bắt đầu học các công cụ bổ sung cho tới khi nào bạn cảm thấy thoải mái với React một cách cơ bản.**

Tôi vẫn nghĩ cách học React đơn giản nhất đó là [tài liệu chính thống](https://facebook.github.io/react/docs/tutorial.html).

## Tìm hiểu về `npm`

`npm` là công cụ quản lý package của Node.js và là phương pháp phổ biến nhất để các lập trình viên front-end và các nhà thiết kế chia sẻ mã nguồn Javascript. Nó bao gồm một hệ thống quản lý module gọi là `CommonJS` và cho phép bạn cài đặt bất cứ công cụ command-line nào được viết bằng Javascript. Hãy đọc [bài này](http://0fps.net/2013/01/22/commonjs-why-and-how/) để biết vì sao `CommonJS` là cần thiết với các trình duyệt, hoặc [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) để biết thêm về `CommonJS` API.

Hầu hết các components, thư viện và công cụ tái sử dụng trong hệ sinh thái của React đều được triển khai như là thành các module `CommonJS` và có thể cài đặt thông qua `npm`.

## Tìm hiểu về các công cụ đóng gói Javascript

Vì một vài lí do kĩ thuật mà module `CommonJS` (ví dụ, các thư viện trên `npm`) không thể sử dụng native trên trình duyệt. Bạn cần có một "công cụ đóng gói" Javascript để "đóng gói" các modules này thành các files `.js` mà có thể include được trên trang web qua thẻ `<script>`.

Một số ví dụ về công cụ đóng gói Javascript bao gồm `webpack` và `browserify`. Cả hai đều là sự lựa chọn tốt, nhưng tôi thích `webpack` hơn vì nó có nhiều tính năng hỗ trợ tốt cho việc xây dựng lớn một cách dễ dàng hơn. Vì tài liệu của nó khá khó hiểu, tôi có tạo ra [template để bắt đầu ngay](https://github.com/petehunt/react-webpack-template) và tôi có viết [hướng dẫn về webpack](https://github.com/petehunt/webpack-howto) với các use cases phức tạp hơn.

Một điều nên nhớ là `CommonJS` sử dụng hàm `require()` để nhập liên kết các modules, vì thế nhiều người trở nên thắc mắc và nghĩ nó có liên quan gì đó tới một project khác có tên là `require.js`. Vì nhiều lý do kĩ thuật, tôi khuyên bạn nên tránh sử dụng `require.js`. Nó cũng không được sử dụng phổ biến trong môi trường của React.

## Tìm hiểu về ES6

Ngoài JSX (mà bạn học trong các hướng dẫn về React), bạn sẽ thấy nhiều cú pháp thú vị trong các ví dụ. Chúng được gọi là ES6, và đó là phiên bản mới nhất của Javascript mà bạn chưa học tới. Vì còn quá mới nên chưa được hỗ trợ trên các trình duyệt, nhưng các công cụ đóng gói sẽ thực hiện phiên dịch với cấu hình đúng cho bạn để có thể sử dụng được trên trình duyệt.

Nếu bạn muốn hoàn thiện nhanh với React, **bạn có thể bỏ qua việc học ES6**, hoặc có thể lựa chọn khi đang làm giữa chừng.

Bạn có thể thấy nhiều hội thảo về lớp trong ES6 là cách tốt nhất để tạo các React components. Điều này là không đúng. Hầu hết mọi người (bao gồm cả Facebook) đang sử dụng `React.createClass()`.

## Tìm hiểu về routing

"Các ứng dụng single-page" trở nên khá rầm rộ ngày nay. Đây là những trang web mà chỉ thực hiện khởi tạo một lần, và khi người dùng ấn vào một đường dẫn hay nút ấn thì Javascript trên trang web sẽ thực thi mà trang web không cần phải reload lại. Việc quản lý địa chỉ trên thanh địa chỉ được thực hiện bởi **router**.

Router được sử dụng phổ biến nhất trong hệ sinh thái React là [react-router](https://github.com/rackt/react-router). Nếu như bạn đang xây dựng một ứng dụng single-page, hãy sử dụng nó trừ khi bạn có lý do mà không thể sử dụng.

**Đừng nên sử dụng router nếu như bạn không xây dựng ứng dụng single-page**. Hầu hết các dự án đều bắt đầu từ một component nhỏ bên trong của một ứng dụng lớn.

## Tìm hiểu về Flux

Chắc hẳn bạn đã từng nghe về Flux. Có **quá nhiều** thông tin không đúng về Flux.

Nhiều người cùng tập hợp lại để xây dựng một ứng dụng và muốn định nghĩa cấu trúc dữ liệu và họ nghĩ sẽ cần sử dụng tới Flux để làm được việc đó. **Tiếp cận Flux như thế là sai. Flux chỉ nên được thêm khi mà các components đã được xây dựng rồi.**

Các components trong React được sắp xếp phân bậc. Phần lớn thời gian, cấu trúc dữ liệu cũng đi theo một cấp. Trong những tình huống này thì Flux không thể giúp được gì nhiều. Tuy nhiên, đôi lúc cấu trúc dữ liệu của bạn lại không theo tầng nào cả. Khi các React components bắt đầu nhận `props` mà có vẻ không liên quan, hoặc bạn có một số lượng nhỏ các components bắt đầu trở nên phức tạp, thì bạn có thể muốn thử với Flux.

**Bạn sẽ biết khi nào bạn cần Flux. Nếu bạn không chắc chắn là bạn cần, thì bạn không cần.**

Một khi bạn đã quyết định sử dụng Flux, sử dụng thư viện phổ biến và đầy đủ tài liệu nhất là [Redux](http://redux.js.org/). Có **rất nhiều** sự lựa chọn khác, và bạn sẽ bị cám dỗ vào việc đi đánh giá so sánh chúng, nhưng lời khuyên của tôi dành cho bạn là chỉ nên chọn với thư viện dược dùng phổ biến nhất.

## Tìm hiểu về inline styles

Trước React, nhiều người tái sử dụng CSS với các định dạng văn bản phức tạp xây dựng qua các tiền xử lý CSS như SASS. Nhưng sau đó React hỗ trợ để tạo các components có thể tái sử dụng một cách đơn giản, các định dạng CSS cũng trở nên đỡ phức tạp. Đa phần trong cộng đồng (bao gồm cả tôi) cũng đang thí nghiệm với việc loại bỏ các định dạng đó.

Đây có thể là một ý tưởng điên rồ vì mấy lí do. Nó làm cho media queries trở nên khó hơn, và có thể sinh ra hạn chế về hiệu năng khi sử dụng kĩ thuật này. **Khi bắt đầu với React, chỉ cần style như bình thường**.

Một khi bạn hiểu được React hoạt động thế nào, bạn có thể thử qua các phương pháp khác. Một phương pháp phổ biến đó là [BEM](https://en.bem.info/). Tôi khuyên các bạn bỏ các tiền xử lý CSS, vì React hỗ trợ bạn một cách tái sử dụng styles tốt hơn và công cụ đóng gói Javascript có thể sinh ra các stylesheets tối ưu hơn (tôi có [chia sẻ này tại OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). React, như bất cứ một thư viện Javascript nào khác, vẫn hoạt động bình thường với các tiền xử lý CSS.

## Tìm hiểu về server rendering

Server rendering thường được gọi là "toàn bộ" hay "đồng bộ" JS. Điều đó có nghĩa là bạn có thể lấy bất cứ React components nào và render chúng thành HTML tĩnh trên server. Điều này cải thiện được tốc độ ban đầu vì người dùng không cần phải chờ JS thực hiện download để có thể thấy được UI ban đầu, và React có thể tái sử dụng HTML đã được render phía server, vì vậy mà không cần xử lý ở phía client.

Bạn cần sử dụng server rendering khi mà bạn thấy việc render ban đầu trở nên quá chậm hoặc bạn muốn cải thiện thứ hạng tìm kiếm. Mặc dù Google bây giờ đã thực hiện index các nội dung render phía client, nhưng tại thời điểm tháng một 2016, mỗi khi được lấy ra đo lường thì thấy rõ thứ hạng bị ảnh hướng đi xuống, có khả năng là do vi phạm về tốc độ render phía client.

Việc render phía server vẫn cần nhiều công cụ để làm cho nó trở nên chính xác. Vì việc này mặc định được hỗ trợ trong các React components mà không cần quan tâm tới việc render phía server, bạn nên xây dựng ứng dụng trước và quan tâm tới việc render phía server sau. Bạn sẽ không cần thiết phải viết lại tất cả các components để xử lý việc dó.

## Tìm hiểu về Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) cung cấp một tập hợp cấu trúc dữ liệu có thể hỗ trợ giải quyết các vấn đề về tối ưu hoá khi xây dựng ứng dụng React. Đấy là một thư viện tuyệt vời, và bạn chắc hẳn sẽ sử dụng khá nhiều khi xây dựng ứng dụng về sau. Tuy nhiên thì nó lại không cần thiết cho tới khi bạn quan tâm tới tối ưu hoá.

## Tìm hiểu về Relay, Falcor etc

Đây là những công nghệ giúp bạn giảm số lượng AJAX requests. Những kĩ thuật này vẫn còn khá là mới mẻ, vì vậy, nếu bạn không có vấn đề với quá nhiều AJAX requests thì bạn không cần tới Relay hay Falcor.
