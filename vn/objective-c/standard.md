## Ngôn ngữ

Về ngôn ngữ sử dụng  chính trong việc đặt tên bthì chúng ta sẽ sử dụng tiếng Anh Mỹ (US English)

**Preferred:**
```objc
UIColor *myColor = [UIColor whiteColor];
```

**Not Preferred:**
```objc
UIColor *myColour = [UIColor whiteColor];
```


## Tổ chức code

Sử dụng `#pragma mark -` để phân loai các methods theo nhóm có chức năng liên quan tới nhau theo cấu trúc chung như sau:

```objc
#pragma mark - Lifecycle

- (instancetype)init {}
- (void)dealloc {}
- (void)viewDidLoad {}
- (void)viewWillAppear:(BOOL)animated {}
- (void)didReceiveMemoryWarning {}

#pragma mark - Custom Accessors

- (void)setCustomProperty:(id)value {}
- (id)customProperty {}

#pragma mark - IBActions

- (IBAction)submitData:(id)sender {}

#pragma mark - Public

- (void)publicMethod {}

#pragma mark - Private

- (void)privateMethod {}

#pragma mark - Protocol conformance
#pragma mark - UITextFieldDelegate
#pragma mark - UITableViewDataSource
#pragma mark - UITableViewDelegate

#pragma mark - NSCopying

- (id)copyWithZone:(NSZone *)zone {}

#pragma mark - NSObject

- (NSString *)description {}
```

## Spacing

* Indent sử dụng 2 spaces. Không sử dụng tabs . Hãy  chắc chắn rằng bạn đã thiết lập ở trong Xcode (Preferences).
* Ngoặc nhọn mở của  (`if`/`else`/`switch`/`while` etc.)  luôn ở  trên cùng 1 dòng với keyword và ngoặc đóng sẽ ở trên dòng mới.

**Preferred:**
```objc
if (user.isHappy) {
  //Do something
} else {
  //Do something else
}
```

**Not Preferred:**
```objc
if (user.isHappy)
{
    //Do something
}
else {
    //Do something else
}
```

* Các methods sẽ phân cách nhau bằng và chỉ 1 dòng trống (blank line).  Có thể sử dụng dòng trống bên trong method để phân cách các  chức năng nhưng  bạn nên tạo method mới nếu có thể.
* Trường hợp sử dụng `@synthesize`  và `@dynamic` thì nên được khai báo trên dòng mới
* Tránh việc căn lề theo dấu hai chấm `:` . Điều đó dôi lúc sẽ làm cho việc đọc code trở lên khó khăn hơn

**Preferred:**

```objc
// blocks dễ đọc hơn
[UIView animateWithDuration:1.0 animations:^{
  // something
} completion:^(BOOL finished) {
  // something
}];
```

**Not Preferred:**

```objc
// căn lề theo dấu hai chấm làm khó đọc code hơn
[UIView animateWithDuration:1.0
                 animations:^{
                     // something
                 }
                 completion:^(BOOL finished) {
                     // something
                 }];
```

## Comments

Trong trường hợp cần sử dụng thì  các comments nên được dùng để giải tích vì sao đoạn code đấy thực thi làm công việc gì. Bất kỳ comment nào cũng cần được cập nhật thường xuyên hoặc xoá đi trong trường hợp không còn cần thiết nữa.

Hạn chế sử dụng  commets dạng block vì các dòng code nên tự mô tả mục đích bởi chính nó. *Ngoại lệ: Điều này không áp dụng cho các comments thường tạo ra tài liệu.*

## Naming

Việc đặt tên nên tuân theo chuẩn của [Apple  (Cocoa)](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-BBCHBFAH)

Tên biến và method nên mô tả rõ ràng (kể cả dài).

**Preferred:**

```objc
UIButton *settingsButton;
```

**Not Preferred:**

```objc
UIButton *setBut;
```

Luôn sử dụng tiền tố với 3 chữ cái  cho  tên class và constant. Tuy nhiên có thể bỏ qua đối với tên các entity của Core Data. Ví dụ đối với các tài liệu, hướng dẫn chính thức của raywenderlich.com thì tiền tố 'RWT' luôn được sử dụng.

Các constants nên được đặt tên theo kiểu CamelCase và có gắn tiền tố liên quan tới tên class để rõ ràng hơn.

**Preferred:**

```objc
static NSTimeInterval const RWTTutorialViewControllerNavigationFadeAnimationDuration = 0.3;
```

**Not Preferred:**

```objc
static NSTimeInterval const fadetime = 1.7;
```

Các properties luôn đặt tên theo camelCase với chữ cái đầu iền được viết thường. Luôn sử dụng auto-synthesis trừ khi bắt buộc.

**Preferred:**

```objc
@property (strong, nonatomic) NSString *descriptiveVariableName;
```

**Not Preferred:**

```objc
id varnm;
```

### Gạch dưới - Underscores

Khi sử dụng các properties, biến instance luôn sử dụng `self.`. thay vì dùng `_`. Ngoại trừ một số trường hợp bắt buộc như trong việc khởi tạo, override setter, getter ...

Biến local không sử dụng gạch dưới.

## Methods

Khi khai báo method, cần có một dấu cách sau method type (ký hiệu -/+). Giữa các đoạn của method nên có dấu cách để phân đoạn. Luôn sử dụng  các từ mô tả rõ ràng ý nghĩa của các argument.

**Preferred:**
```objc
- (void)setExampleText:(NSString *)text image:(UIImage *)image;
- (void)sendAction:(SEL)aSelector to:(id)anObject forAllCells:(BOOL)flag;
- (id)viewWithTag:(NSInteger)tag;
- (instancetype)initWithWidth:(CGFloat)width height:(CGFloat)height;
```

**Not Preferred:**

```objc
-(void)setT:(NSString *)text i:(UIImage *)image;
- (void)sendAction:(SEL)aSelector :(id)anObject :(BOOL)flag;
- (id)taggedView:(NSInteger)tag;
- (instancetype)initWithWidth:(CGFloat)width andHeight:(CGFloat)height;
- (instancetype)initWith:(int)width and:(int)height;  // Never do this.
```

## Variables - Biến

Các biến nên được đặt tên càng mô tả rõ ràng càng tốt. Không dùng biến một chữ cái ngoại trừ trong vòng lặp `for()`.

Dấu sao (`*`) đặt cạnh tên biến. Ví  dụ `NSString *text` chứ không phải`NSString* text` hay `NSString * text`.

## Property Attributes

Property attributes nên được liệt kê một cách rõ ràng để giúp cho các lập trình viên mới có thể đọc hiểu một cách dễ dàng. Thứ tự của các attributes nên là  tính storage rồi mới đến tính atomicity.

**Preferred:**

```objc
@property (weak, nonatomic) IBOutlet UIView *containerView;
@property (strong, nonatomic) NSString *tutorialName;
```

**Not Preferred:**

```objc
@property (nonatomic, weak) IBOutlet UIView *containerView;
@property (nonatomic) NSString *tutorialName;
```

## Dot-Notation Syntax

Dùng dấu chấm (Dot-notation) trong mọi trường hợp có thể. Điều này sẽ làm code ngắn gọn hơn. Những trường hợp không thể  thì mới dùng ngoặc vuông.

**Preferred:**
```objc
NSInteger arrayCount = self.array.count;
view.backgroundColor = [UIColor orangeColor];
UIApplication.sharedApplication.delegate;
```

**Not Preferred:**
```objc
NSInteger arrayCount = [self.array count];
[view setBackgroundColor:[UIColor orangeColor]];
[UIApplication sharedApplication].delegate;
```

## Literals

Luôn sử dụng  literals khi khai báo instances của các kiểu `NSString`, `NSDictionary`, `NSArray`, và `NSNumber`. Chú ý rằng `nil` sẽ không được truyền vào `NSArray` và `NSDictionary` literals vì chúng sẽ gây ra crash.

**Preferred:**

```objc
NSArray *names = @[@"Brian", @"Matt", @"Chris", @"Alex", @"Steve", @"Paul"];
NSDictionary *productManagers = @{@"iPhone": @"Kate", @"iPad": @"Kamal", @"Mobile Web": @"Bill"};
NSNumber *shouldUseLiterals = @YES;
NSNumber *buildingStreetNumber = @10018;
```

**Not Preferred:**

```objc
NSArray *names = [NSArray arrayWithObjects:@"Brian", @"Matt", @"Chris", @"Alex", @"Steve", @"Paul", nil];
NSDictionary *productManagers = [NSDictionary dictionaryWithObjectsAndKeys: @"Kate", @"iPhone", @"Kamal", @"iPad", @"Bill", @"Mobile Web", nil];
NSNumber *shouldUseLiterals = [NSNumber numberWithBool:YES];
NSNumber *buildingStreetNumber = [NSNumber numberWithInteger:10018];
```

## Enumerated Types

Khi sử dụng các `enum`, nên sử dụng kiểu khai báo mới với `NS_ENUM()`

**Ví dụ:**

```objc
typedef NS_ENUM(NSInteger, RWTLeftMenuTopItemType) {
  RWTLeftMenuTopItemMain,
  RWTLeftMenuTopItemShows,
  RWTLeftMenuTopItemSchedule
};
```

```objc
typedef NS_ENUM(NSInteger, RWTGlobalConstants) {
  RWTPinSizeMin = 1,
  RWTPinSizeMax = 5,
  RWTPinCountMin = 100,
  RWTPinCountMax = 500,
};
```

Nên tránh kiểu định nghĩa k-style cũ trừ khi bạn đang viết code CoreFoundation C

**Not Preferred:**

```objc
enum GlobalConstants {
  kMaxPinSize = 5,
  kMaxPinCount = 500,
};
```


## Câu lệnh Case - Switch

Khi câu lệnh case nhiều hơn một dòng thì nên dùng ngoặc nhọn để bao lại.

```objc
switch (condition) {
  case 1:
    // ...
    break;
  case 2: {
    // ...
    // Multi-line example using braces
    break;
  }
  case 3:
    // ...
    break;
  default: 
    // ...
    break;
}

```

Khi sử dụng kiểu enumerated cho switch, 'default' case là không cần thiết Ví dụ:

```objc
RWTLeftMenuTopItemType menuType = RWTLeftMenuTopItemMain;

switch (menuType) {
  case RWTLeftMenuTopItemMain:
    // ...
    break;
  case RWTLeftMenuTopItemShows:
    // ...
    break;
  case RWTLeftMenuTopItemSchedule:
    // ...
    break;
}
```


## Private Properties

Private properties nên được khai báo ở trong class extensions (anonymous categories) của file implementation (file .m).

**Ví dụ:**

```objc
@interface RWTDetailViewController ()

@property (strong, nonatomic) GADBannerView *googleAdView;
@property (strong, nonatomic) ADBannerView *iAdView;
@property (strong, nonatomic) UIWebView *adXWebView;

@end
```

## Booleans

Objective-C sử dụng `YES` và `NO`.  Do đó `true` và `false` chỉ nên sử dụng khi code CoreFoundation, C hoặc C++.  Vì `nil` cũng có thể coi như là `NO` nên không cần so sánh nó ở trong câu điều kiện. Không bao giờ so sánh trực tiếp bất cứ thứ gì với `YES`.

**Preferred:**

```objc
if (someObject) {}
if (![anotherObject boolValue]) {}
```

**Not Preferred:**

```objc
if (someObject == nil) {}
if ([anotherObject boolValue] == NO) {}
if (isAwesome == YES) {} // Đừng bao giờ làm thế này.
if (isAwesome == true) {} // Đừng bao giờ làm thế này.
```

Nếu một property kiểu `BOOL` được  biểu diễn như là một tính từ thì tiền tố “is” có thể bỏ qua ở định nghĩa nhưng nên được đặt  đặc biệt cho getter:

```objc
@property (assign, getter=isEditable) BOOL editable;
```
Tham khảo và ví dụ được lấy từ [Cocoa Naming Guidelines](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingIvarsAndTypes.html#//apple_ref/doc/uid/20001284-BAJGIIJE).

## Câu điều kiện

Phần code thực thi của câu điều kiện phải luôn được bao bởi ngoặc nhọn ngay cả khi nó có thể viết mà không cần để tránh các lỗi có thể xảy ra. Các lỗi này có thể là việc thêm 1 dòng lệnh nữa vào và nghĩ rằng nó vẫn ở trong câu lệnh điều kiện if. Ngoài ra còn có thể là các lỗi như việc comment câu thực thi của điều kiện if khiến cho câu lệnh tiếp theo trở thành câu thực thi, điều này sẽ xảy ra các lỗi không lường trước được như [ở đây](http://programmers.stackexchange.com/a/16530).  Việc luôn sử dụng ngoặc nhọn đối với câu điều kiện cũng đảm bảo style thống nhất và việc giải quyết khi có các conflict (làm việc với các source control) cũng trở lên dễ dàng hơn.

**Preferred:**
```objc
if (!error) {
  return success;
}
```

**Not Preferred:**
```objc
if (!error)
  return success;
```

hoặc

```objc
if (!error) return success;
```

### Toán tử điều kiện

Chỉ nên sử dụng toán tử điều kiện `?:` khi nó làm cho dòng code gọn gàng và dễ hiểu hơn. Nên sử dụng toán tử điều kiện khi chỉ có một điều kiện. Đối với câu có nhiều điều kiện, thì dùng câu lệnh if sẽ rõ ràng hơn. Nhìn chung toán tử điều kiện thường được sử dụng trong việc gán giá trị cho biến mà phụ thuộc vào điều kiện nào đó.

Biến không phải dạng boolean nên được so sánh với một giá trị cụ thể và sử dụng ngoặc đơn để khiến cho dòng lệnh dễ đọc hơn. Nếu giá trị được so sánh là kiểu boolean thì ngoặc đơn là không cần thiết.

**Preferred:**
```objc
NSInteger value = 5;
result = (value != 0) ? x : y;

BOOL isHorizontal = YES;
result = isHorizontal ? x : y;
```

**Not Preferred:**
```objc
result = a > b ? x = c > d ? c : d : y;
```

## Init Methods

Init methods nên tuân theo chuẩn được cung cấp sẵn bởi mẫu code của Apple. Kiểu trả về nên là `instancetype` thay vì kiểu `id`

```objc
- (instancetype)init {
  self = [super init];
  if (self) {
    // ...
  }
  return self;
}
```

## Class Constructor Methods

Khi sử dụng class constructor methods, kiểu trả về phải luôn luôn là `instancetype`, không bao giờ sử dụng `id`

Where class constructor methods are used, these should always return type of 'instancetype' and never 'id'. Điều này sẽ giúp cho trình biên dịch sẽ gợi ý đúng kiểu trả về. Như trong ví dụ dưới, trình biên dịch sẽ biết kết quả trả về là 1 instance của Airplane

```objc
@interface Airplane
+ (instancetype)airplaneWithType:(RWTAirplaneType)type;
@end
```

Xem thêm thông tin tại [NSHipster.com](http://nshipster.com/instancetype/).

## Golden Path

Khi code với các câu điều kiện, phần lề phía bên tay trái của code được coi là "golden"  hay "happy" path. Điều đó có nghĩa là không "nest" các câu `if`. Sử dụng nhiều cầu `return` là chấp nhận được.

**Preferred:**

```objc
- (void)someMethod {
  if (![someOther boolValue]) {
	return;
  }

  //Do something important
}
```

**Not Preferred:**

```objc
- (void)someMethod {
  if ([someOther boolValue]) {
    //Do something important
  }
}
```

## Xử lý lỗi

Khi methods trả về tham số error theo reference, nên switch dựa trên giá trị trả về thay vì biến error

**Preferred:**
```objc
NSError *error;
if (![self trySomethingWithError:&error]) {
  // Handle Error
}
```

**Not Preferred:**
```objc
NSError *error;
[self trySomethingWithError:&error];
if (error) {
  // Handle Error
}
```

Nguyên nhân là do một số APIs của Apple sẽ ghi những giá trị rác lên tham số error trong trường hợp thành công, nên switch dựa trên biến error có thể dẫn tới phủ định sai và sau đó gây crash.

## Singletons

Singleton objects nên sử dụng thread-safe pattern để tạo các shared instance.
```objc
+ (instancetype)sharedInstance {
  static id sharedInstance = nil;

  static dispatch_once_t onceToken;
  dispatch_once(&onceToken, ^{
    sharedInstance = [[self alloc] init];
  });

  return sharedInstance;
}
```
Tham khảo thêm [ở đây](http://cocoasamurai.blogspot.com/2011/04/singletons-your-doing-them-wrong.html).


## Line Breaks - Xuống dòng

Việc xuống dòng là một vấn đề khá quan trọng trong bản style guide này vì nó ưu tiên cho việc dễ in và dễ đọc trực tiếp (trên github chẳng hạn) thay vì phải mở xem trong các editor (như Xcode)

Ví dụ:
```objc
self.productsRequest = [[SKProductsRequest alloc] initWithProductIdentifiers:productIdentifiers];
```
Một câu lệnh dài như trên có thể tách ra làm hai dòng với dòng thứ hai thụt vào hai dấu cách (theo quy định ngay từ đầu với dấu cách - Spacing) như sau
```objc
self.productsRequest = [[SKProductsRequest alloc]
  initWithProductIdentifiers:productIdentifiers];
```

Bản Style Guide này được tham khảo trực tiếp từ style guide của raywenderlich với các chỉnh sửa cần thiết trong quá trình sử dụng thực tế. Ngoài ra bạn cũng có thể tham khảo thêm các style guides khác ben dưới đây

# Other Objective-C Style Guides

* [Robots & Pencils](https://github.com/RobotsAndPencils/objective-c-style-guide)
* [New York Times](https://github.com/NYTimes/objective-c-style-guide)
* [Google](http://google-styleguide.googlecode.com/svn/trunk/objcguide.xml)
* [GitHub](https://github.com/github/objective-c-conventions)
* [Adium](https://trac.adium.im/wiki/CodingStyle)
* [Sam Soffes](https://gist.github.com/soffes/812796)
* [CocoaDevCentral](http://cocoadevcentral.com/articles/000082.php)
* [Luke Redpath](http://lukeredpath.co.uk/blog/my-objective-c-style-guide.html)
* [Marcus Zarra](http://www.cimgf.com/zds-code-style-guide/)
