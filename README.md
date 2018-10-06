# Way-For-OOD-Analysis

## 如何进行面向对象的分析

### 找出最关键的业务场景

> 通过业务中的动词描述进行寻找

1. 学生参加一门课的考试  ->  考试就是业务场景
2. 学生去图书馆借书 -> 借书就是业务场景
3. 学生去图书馆还书 -> 还书就是业务场景
4. 早晨去公司打卡 -> 打卡就是业务场景
5. 中午在公司刷卡吃饭 -> 吃饭就是业务场景

### 针对每个业务场景分析出场景的参与者

> 以对象形式参与业务场景的参与者

> 以服务形式参与业务场景的参与者

#### 之所以区分两者的原因是

1. 服务并不关心参与者是具体的某个对象`(换言之就是无状态)`,而只关心参与者是在系统中是何种服务
2. 对象则是关心参与者是某个具体的对象,也就是关心参与者是谁

### 分析每个场景内参与者的基本状态特征

> 基本状态特征是指对象与生俱来的一开始被创建出来之后就具有的状态特征

> 比如人的身高和体重就是人与生俱来的基本状态特征, 只要你是人你就一定会拥有这两个状态特征, 即使这两个状态特征会随着时间的推移发生数值的变化

> 再比如说这篇文字在撰写之时即拥有了内容这个基本状态特征, 只是内容这个基本状态特征可以在任何时间进行修改; 同样这篇文字也拥有创建时间这个基本状态特征,但是这个状态特征是无法修改的

> 值得注意的是某些与对象相关联的信息并不属于基本状态特征, 比如某开发人员参加了cisco资格认证考试并取得了资格证书, 那么该对象和证书之间存在了一对一的拥有关系, 这个证书也成为了该开发人员的状态特征, 但是这个状态特征并不是与生俱来的基本状态特征而是通过后天考试得来的产物所以它不是基本状态特征

### 分析每个场景参与者对象分别扮演的角色,整个场景的完整交互过程,对象在参与场景的过程中执行的交互行为

> 这个过程涉及到对象之间如何交互,涉及到如何分析特定对象的交互行为, 从而最终决定了在编码层次上具体类包含的具体行为

> 分析的重点在于将整个业务场景中的每个交互行为通过四色原型的分析方法来理解`一个什么样的人或组织或物品以某种角色在某个时刻或某段时间内参与某个活动`

> 同样也可以通过分析`交互行为是谁通知谁做什么事情`, 一般而言行为的驱动者就是通知方,行为的执行者就是被通知方,被通知方拥有`通知方要求做的事`的执行行为

> 需要注意区分的是现实生活中的对象并不是扮演了某个角色后才具有角色所定义的某种行为,而是固有存在的,只不过是在扮演角色后表现出了该行为, 因此对于现实生活中的对象,执行角色所定义的行为和扮演角色是同时发生的,没有谁先谁后的说法(正如学生之于学习和考试, 并没有谁先谁后的区分)

> 但是软件中的对象则不同,因为软件中的对象只是现实生活中的对象的某一方面, 它的作用是专而精而不是大而全

> 另外从设计实现的角度以职责单一的标准来看待软件中的对象时,也不会将软件中的对象设计的很复杂,包含多个职责,因为这样会导致对象难以维护,

> 给软件中的对象赋予多个角色或多个指责的方式虽不违背分析原则,但`违背设计原则`

> 软件中的对象往往是设计成`当它扮演某个角色时`,`动态给对象注入角色所定义的交互行为`,从而给对象`赋予了参与场景交互的能力`

> 简而言之,软件中的对象,`平时只具有基本的状态特征和基本的非交互行为`,而当它`扮演某个角色时`,则`动态具有交互行为`

### 分析如何记录和跟踪某次交互行为,分析该交互行为会产生哪些额外的信息

> 上述我们提到某开发人员通过参加cisco资格考试获得了某资格证书, 证书成为了其的状态特征但非基本状态特征的过程, 由此引入`一次对象的交互活动会产生一些与该交互活动相关的交互信息`

> 除了上述的例子外,很容易会联想到学生考试会获得考试成绩的状态信息, 员工吃饭会产生所选菜色和花费金额的状态信息, 市民借书产生的借阅信息

> 在某些情况下,这些状态信息可能会在之后被持续维护和更新,比如学生参加考试前考试得分是null但是参与之后会更新考试得分的状态信息,再比如市民借书所产生的还书时间这一状态信息随着时间的推移才会产生

> 从这些规律中可以发现`交互是一个过程`,并且该过程一旦开始后就会`产生一些相关的信息`,如考试的成绩,借阅信息的归还时间等

> 通常分析时会把交互过程本身所涉及的一切信息以及交互过程所产生的所有附加信息作为一个整体来进行考虑, 但是这样具有一个高耦合度

> 此时设计一个对象,用来表示某一次交互的结果,这个结果包含交互过程本身所涉及的一切信息以及交互过程所产生的所有附加信息会是一个更加合理的方案

> 在交互行为结束后设计一个对象用来`表示一次交互活动的相关信息`,这些信息一方面体现了`交互活动的参与者`(交互时间,交互地点),另一方面体现了`交互活动所产生的附加的信息`

> 之所以将这些随着交互产生的信息定义为对象而不是值对象, 是因为这些信息并不是不可改变的内容, 相反这些信息更有可能在后续的交互过程中被更新

### 图书管理系统场景举例

#### 图书信息入库场景(假设)

> 图书馆管理员扫描不同名称的书本的过程

> 每本书都有一个ISBN,即`International Standard Book Number` - `国际标注书号`

> 图书馆通过ISBN来管理书本,同一个ISBN的书可能有很多不同的副本,每一个副本就是一本真实存在书

> 严格来说图书馆数据库中保存的是`书本的库存信息`

> 在图书入库的场景中对于ISBN相同,即书名相同的书只会被扫描一次,管理员会输入这种书总共有多少本,应该放在什么地方等相关的库存信息

#### 借书场景(假设)

> 借书人持图书卡去图书馆,找到要借的书(单/复数),带着书去借书处借书

> 图书管理员扫描借书人的借书卡以及书本的条形码,条形码就是ISBN

> 借书人借到书

#### 还书场景(假设)

> 借书人携带图书卡去图书馆,于还书处还书

> 图书管理员扫描还书人的借书卡以及书本的条形码,如果有需要罚款的部分会同时计算

> 还书人完成还书

#### 图书入库场景的分析

##### 场景参与者

1. 图书馆`图书馆在整个图书借阅系统中只需要一个实例,且场景中并不在意是具体哪个图书馆, 故而设计成服务更为合理`
2. 书本

##### 参与者基本状态特征

1. 书本的基本状态特征(书名,作者,ISBN出版社等)
2. 图书馆的基本状态特征(`图书馆作为服务没有基本状态特征,也就是无状态,服务只提供服务性质的行为`)

##### 场景交互过程分析

1. 图书馆本身就具有图书入库的行为
2. 图书入库时,图书馆服务会生成并保存一个书本的`库存信息`,该信息包含了`某个名称的书本的数量`,`书架位置信息`
3. 该库存信息中的`Count`表示`某个名称的书共有几本`,当在借书或还书的场景发生时,这个Count就会改变

```typescript
public class StoreBookContext {
    private library: ILibraryService;
    private book: Book;
    constructor(
        private library: ILibraryService,
        private book: Book
    ) {
        this.library = library;
        this.book = book;
    }
    public Interaction(count: number,location: string): void{
            this.library.StoreBook(this.book, count, location);
    }
}

public class ILibraryService {
    constructor(
        private bookStoreInfo: BookStoreInfo,
        private bookStoreInfoRepository: BookStoreInfoRepository
    ) {}
    public StoreBook(book: Book,count: number,location: string): void{
    //图书入库时生成图书的库存信息
        const bookStoreInfo = new BookStoreInfo(book, count);
        bookStoreInfo.Location = location;
        bookStoreInfoRepository.Add(bookStoreInfo);
    }
}
// 交互之后,场景参与者的基本状态特征没有发生改变
```

#### 借书场景分析

##### 场景参与者

1. 图书馆注册帐号`借书人只是一个角色, 注册帐号扮演了借书人这个角色后可以行驶借书的行为`
2. 图书馆`服务`
3. 书本`值对象`

##### 参与者基本状态特征

1. 书本的基本状态特征`(书名,作者,出版社等)`
2. 图书馆的基本状态特征`(服务是无状态的)`
3. 注册帐号的基本状态`(卡号,所有者姓名,是否锁定)`

##### 场景交互过程分析

> 某个软件的使用者,即软件用户通过某个已注册帐号登录软件系统,选择想借的书之后点击“借书”按钮,该按钮触发一个借书的场景

> 该场景创建时包含了部分的场景参与者,在借书这个例子中就是帐号和书,借书场景中帐号扮演借书者这个角色,帐号在扮演了借书者这个角色后对每一本书行驶借书的交互行为

> 扮演了借书者角色的注册帐号自动具有了借书的行为,在该行为的内部实现中,通知图书馆把书借出来

> 随后图书馆作为服务接到通知后,首先根据当前书本获取书本的库存信息,如果当前库存信息是0本,说明这本书没有库存,就抛出异常通知软件使用者这本书目前无法借出

> 如果还有库存,则先更新库存信息,比如图书的数量减1,然后根据当前借书人,书本,以及当前时间生成一个借书信息对象,该对象可能还会包含一个理论图书归还时间的附加信息。最后将该借书信息对象保存起来

```typescript
 public class BorrowBooksContext
    {
        private account: LibraryAccount;
        private books: Array<Book>;

        public BorrowBooksContext(account: LibraryAccount, books: Array<Book>)
        {
            this.account = account;
            this.books = books;
        }

        public void Interaction()
        {
            const borrower = account.ActAs<IBorrower>();
            this.books.forEach(book => {
                borrower.BorrowBook(book);
            })
        }
    }
public void BorrowBook(book: Book)
{
    //通知图书馆把书借给我
    library.LendBook(book, this);
}
public void LendBook(book: Book, borrower: IBorrower)
{
    //更新书本在图书馆的库存信息,如：数量信息、所在书架位置信息
    const bookStoreInfo = bookStoreInfoRepository.GetBookStoreInfo(book.Id);
    if (bookStoreInfo.Count == 0)
    {
        throw new Exception(string.Format("The count of book '{0}' in library is zero, so you cannot borrow it.", book.BookName));
    }
    bookStoreInfo.DecreaseCount(); //数量减1
    bookStoreInfo.Location = null; //位置清空

    //生成借书信息并保存到Repository中
    borrowInfoRepository.Add(new BorrowInfo(book, borrower, DateTime.Now));
}
// 交互之后,场景参与者的基本状态特征没有发生改变
```

#### 还书场景分析

##### 与借书类似的过程

1. 注册帐号扮演借阅者角色执行还书行为
2. 执行过过程中通知图书馆接收某本要归还的书
3. 图书馆接到通知后调出与该书本对应的那一次借书信息并更新其还书时间
4. 最后更新图书的库存信息

```typescript
  public class ReturnBooksContext
    {
        private account: LibraryAccount;
        private books: Array<Book>;

        public ReturnBooksContext(account: LibraryAccount, books: Array<Book>)
        {
            this.account = account;
            this.books = books;
        }

        public void Interaction()
        {
            const returnner = account.ActAs<IBorrower>();
            this.books.forEach(book => {
                returnner.ReturnBook(book);
            })
        }
    }
public void ReturnBook(book: Book)
{
    //通知图书馆接收我要归还的书
    library.ReceiveReturnedBook(book, this);
}
public void ReceiveReturnedBook(book: Book, borrower: IBorrower)
{
    //设置借书信息的还书时间
    const borrowedInfo = borrowInfoRepository.FindNotReturnedBorrowInfo(borrower.Id, book.Id);
    borrowedInfo.ReturnTime = DateTime.Now;

    //真正的系统还会计算归还时间是否超期,计算罚款之类的逻辑
    // ...
    //这里只更新书本的数量信息,因为还书时并不是马上把书本放回书架的,所以此时书本的书架位置信息还是保留为空
    //等到我们将这本书放到书架的某个位置时,才会更新其位置信息
    var bookStoreInfo = bookStoreInfoRepository.GetBookStoreInfo(book.Id);
    bookStoreInfo.IncreaseCount(); //数量加1
}
```