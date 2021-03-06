# SavingsAccount

## c++作业

一个人可以有多个活期储蓄账户，一个活期储蓄账户包括账号（id）、余额（balance）、年利率（rate）等信息，还包括显示账户信息（show）、存款（deposit）、取款（withdraw）、结算利息（settle）等操作。为此，设计一个类SavingsAccount，将id，balance，rate均作为其数据成员，将show，deposit，withdraw，settle均作为其成员函数。

无论是存款、取款还是结算利息，都需要修改当前的余额并且将余额的变动输出，这些公共操作由私有成员函数record来执行。

实现该类的难点在于利息的计算。由于账户的余额是不断变化的，因此不能通过余额与年利率相乘的办法来计算年利，而是需要将一年当中每天的余额累积起来再除以一年的总天数，得到一个日均余额，再乘以年利率。为了计算余额的按日累计值，SavingsAccount类引入了私有数据成员lastDate，accumulation和私有成员函数accumulate。lastDate用来存储上一次余额变动的日期，accumulation用来存储上次计算利息以后直到最近一次余额变动时余额按日累加的值，accumulate成员函数用来计算截至指定日期的账户余额按日累积值。这样，当余额变动时，需要做的是将变动前的余额与该余额所持续的天数相乘，累加到accumulation中，再修改lastDate。

为简便起见，该类中的所有日期均用一个整数来表示，该整数是一个以日为单位的相对日期，例如如果以开户日为1，那么开户日后的第3天就用4来表示，这样通过将两个日期相减就可以得到两个日期相差的天数，在计算利息时非常方便。

设计并实现该类，并在主函数中实例化对象（建立账户），对账户进行存钱、取钱、计算利息等业务。

对上一个“个人银行账户管理程序”，为SavingsAccount类增加一个静态数据成员total，用来记录各个账户的总金额，并为其增加相应的静态成员函数getTotal用来对其进行访问。

在SavingsAccount类中，对getBalance，getId，getRate，show，accumulate这些不需要改变对象状态的成员函数声明为常成员函数。

要求：SavingsAccount类的定义放在account.h头文件中，类的实现代码放在account.cpp源文件中，main()函数单独放在一个源文件中。
