[About Me](./aboutme.md)

## 反向传播

反向传播算法是现代神经网络算法中最重要的一环，它完成了从错误向正确优化这个过程。表现最好、最优秀，能处理复杂任务的模型无一不使用反向传播算法。

但是，从模拟人脑的角度来看，如果把神经网络比作大脑的神经元连接，那反向传播这个过程对应着大脑的哪种活动呢？人的大脑并没有一个天然的数值计算系统，即使是一加一等于二也是后天的强制模拟。大脑无法完成反向传播中密集的导函数运算，完成梯度更新（也就是神经元更新）。

虽然反向传播算法在实际应用中取得了辉煌的成绩，但还是很难让人相信大脑是通过链式法则的反向传播来完成神经元更新的。

个人认为，大脑中不存在反向传播这个过程，至少不存在按照链式法则进行反向传播的过程。大脑学习的过程更像是一个单向的过程：输入-> 神经元权重更新。在输入的时候，大脑神经元就已经完成了相应的变化。你输入的哪种 case 越多，大脑就更倾向于那种 case 的状态。

反向传播是在正向传播完成后，将结果与实际结果相比较，得到差值，再反向网络传播更新参数。以手被开水烫伤为例。当我们大脑操控手去触摸开水时，大脑首先完成一系列思维传导过程，当手被烫到时，反向传播算法认为，手被烫伤和大脑预期的结果不服，此时计算（被烫伤这个 actual result 和 predict value 的差值，然后使用反向传播更新神经元参数，使得大脑下次遇到这种情况尽可能不会再操控手去触摸开水。但是问题在于尚不清楚大脑是如何完成反向传播的。

我这里提出一种大脑仅凭正向传播完成神经元更新的思路：首先大脑神经元发送一系列指令指挥手去触摸开水，当碰到开水时，大脑意识到这是个错误的行为，终止活动。此时大脑接收到一个信号--"用手去摸开水是一个 bad behavior"，然后大脑将 "用手去摸开水是一个 bad behavior" 这个事实再次在大脑中完成一次正向传播，告诫大脑触摸开水是不对的，更新神经元参数。也就是说，使用两次正向传播来代替现有神经网络中的一次正向传播和一次反向传播。在第一次正向传播后，得到 actual value 和 predict value 的差值之后，反向传播算法选择了链式法则的逆向更新参数，而此处我设想使用第二次正向传播，只不过第二次正向传播的输入和第一次正向传播的输入并不相同，这取决于第一次正向传播后 actual value 和 predict value 之间的差值：如果完全相反，那么第二次正向传播的输入也和第一次正向传播的输入相反。

此处就遇到了两次正向传播中的最大问题：大脑如何表示“用手去摸开水是一个 bad behavior" 呢？当 actual value 和 predict value 重合70%的时候，大脑又如何表示呢？两次正向传播将反向传播的难点从链式法则更新参数变成了如何塑造第二次正向传播的输入。但是对于大脑而言，这依然比严格按照求导法则的反向传播可行得多。

目前反向传播算法已经暴露出来的问题：
1. 学习效率低，优化目标函数非常复杂
2. 需要大量算力

最近一段时间大模型的成功一方面让我们看到了通用人工智能的可能性，但另一方面其巨大的硬件和算力需求也让人叹为观止。我们迟早要寻找更有效的算法。我不想说实现通用人工智能就一定需要模拟人类大脑的行为，我们当然可以另辟蹊径。但是，考虑到人类大脑目前的高超能力和极低的功耗、极高的信息密度，我们很难不认为经历了数百万年进化的人脑就是最接近最优解的那个解。

## 什么是意识

哲学上有个问题一直充满争议：人是否真的拥有自我意识？维基百科上对于人的意识的定义：（人类个体）对（其）内部和外部存在的感知或认识。其实这个定义说的是废话，因为”感知“和”认识“这两个词的定义也很模糊。对于感知这个词，向日葵随着太阳光线变化而旋转算不算一种感知？秋天树叶掉落是不是一种感知？有些人说不是，向日葵旋转是因为自身的某种生长素的释放，树叶落叶可能是低温导致某些结构坏死，变性：这都是一些普通的物理化学变化。但是人也是由普通物质构成，大脑的运转也遵循物理化学变化，遵循因果律。所以人对于外界的感知和反馈和向日葵本质上没有什么区别。

但人的意识神奇在于它能意识到自己有意识，也就是它能感知到自己对于外部变化产生了感知，这也就是我们能”思考为什么我们能思考“，能”意识到我们有意识“。狭义上来讲，我们如今所说的意识，应当是“能感知和认识到自己有感知和认识的能力”。

但其实再仔细深入想想，这种所谓高级的人的意识相对于向日葵那种简单感知并不是什么质的飞跃。意识到自己有意识，可以类比于普通函数和递归函数的区别。普通函数只会执行外部输入给出输出，递归函数的某阶段输入可以作为自己的输入。


## 混沌系统

理想状态下，太阳绕着地球转动，双星系统能保持稳定。而其他行星和天体的存在，很明显让太阳系变成了一个混沌系统。地球绕太阳的旋转不是一个完美的椭圆。按照混沌学的理论，局部微小的影响可能最终对整体产生极大的影响。那么地球等行星是如何在这样一个混沌系统中保持长时间的稳定？这种稳定已经持续了数十亿年，而且丝毫没有崩溃的迹象。

一种可能的解释是，太阳占太阳系总质量的99.8%，其他行星之间的相互作用非常微小，所以能保持稳定。但这种说法本身又和混沌理论相悖--还是那句话：局部微小的影响可能会对整体产生极大的影响。

## 心脏为什么长在左侧

心脏作为有一定质量的器官，持续地跳动，并为身体输送新鲜血液，无论是从身体平衡还是从同时均匀地向身体两侧输血这个角度，都应该放置在人体的中间位置。
身体的胸腔和腹腔空间是有限的，不可能把所有单体内脏器官都放在正中间，分散开来放未尝不可。但是心脏对身体的影响力远非其他器官可比，对身体影响力最大的器官（心脏、大脑、生殖系统）理应都放在身体中间。

## 黑箱

对于较为复杂的DNN，一般认为存在“黑箱问题”，即不清楚其内在逻辑和结果成因，“知其然而不知其所以然”。但是我自己一直反对用“黑箱”这个词来形容神经网络，因为神经网络的每个结构我们都知道得一清二楚--神经网络是我们一个一个公式推导出来的，一行一行代码敲出来的：每一个循环，每一次逻辑判断我们都清楚得知道这些数据产生了什么变化。

但是，依然会有人跳出来反驳：即使你知道每一步干了什么，但是你不知道为什么要这样干。对于一些基本操作，比如Softmax, ReLU, 我们已经很清楚它们的意义是什么，但是对于一些更加抽象的操作（比如多层卷积），可能直观上很难明白每次卷积到底对最后的结果有什么作用。

从这个角度来说，就涉及到黑箱的定义问题：我所认为的黑箱，是类似于人类大脑结构一样不为人所知。而神经网络不同，所有结构清清楚楚，只是由于神经网络实在是过于复杂，一个变量可能要经过上千万次函数映射，以至于人无法直观理解从输入到输出这个漫长的过程。注意，这里说的依然是指人目前无法理解，不表示这就是不可理解的。

有一个很形象的类比是：多层神经网络好比一个复杂的光学镜头，由很多层镜头组成，有些镜头完成偏折，有些镜头完成过滤，有些镜头完成聚焦，最终构成了一套精密的光学系统。如果你要问某一层镜头的某个局部对光线的最终效果产生了什么效果，可能没人能回答上来--我们只需要知道每一层是干嘛的，宏观上层与层之间的关联就行了。问某一个局部对于结果的作用是没有意义的，而且人也无法直观理解。

## Exercise or not, that is a question

Exercise is the most controversial part of human body optimization. Even whether exercise is beneficial if full of controversial. All words in this part are paltry advice. Every should try to exercise to find their own way.

The following will start from my personal experience:

> I don't exercise currently, but I exercised a lot in the past. Before, my daily exercise plan is:
> - Running 10 kms
> - Pull up 5 groups, 5 for each group
> - Sit up 3 groups, 30 for each group
> - Push up 3 groups, 20, 15 and 10 for each group

> These exercise will take about one and a half hour to finish. I usually start exercise at 5 p.m. and with an empty stomach.

> The effect of exercise was significant: My weight dropped quickly, I felt as light as a swallow, vigorous, energetic. I can easily sit 20 pull ups at a time, or run 5 kilometers in 20 minutes. It was amazing.

> And The most important part is psychological: The confidence that exercise brings to me and the pure happiness that dopamine releases during exercise are the real meaning of exercise.

> Exercising is really a cool thing.

And why did i give up exercising finally? Let me continue.

> Later, I travelled to a coastal city for about a month. During that time, I did not keep exercising, Then it was winter, and i was going to continue my exercise like before. But when I tried to running 10 km again, I felt wrong: I did not run as easily as before, but very hard. After running for two laps, I was out of breath. Only two month passed, my running level dropped quickly.

> I started questioning myself: what was the meaning of my running before?

> I realized that exercise is an activity that you must keep throwing your energy into. You just can't stop. 

> **That is, exercise is meaningful and beneficial only if you persist in it, and the process of persistence is enjoyment. Once you stop exercising, your body will gradually return to the state before you start exercising, and all the exercises in the past become worthless.**

> That was my experience.

The essence of exercise is to let us get out of our usual comfort zone. But comfort itself is not a bad thing. 

Exercise itself is painful and against human nature. Think about it: When you walk out of your warm room, the cold wind outside is bitting your bones, and you have to run around the playground for more than a dozen times, what is your purpose of exercising? 

For happiness? No, because when you walk into the cold wnd and start exercising, feel tired again and again, in fact, you are in pain.

For a strong body? No, because when you stop exercising, your body will gradually adapt to daily life instead of strenuous exercise. Finally, your body will become the same before you exercise. 

Again, **exercise is only beneficial and meaningful when you keep doing it.**

### A personal view
To sum up, here are the points why I have a doubt on the necessity of exercise:
- Whether exercise will accelerate or dalay aging remains controversial. 
- Exercise is a long process. If give up, all the exercises in the past will be worthless.
- Exercise is against human nature. It pulls us out of our normal life. It make you feel tired, may even affect your study or work.
- Exercise takes us a lot of time. An hour of exercise may lead to time spent on preparing equipments, commuting and taking a bath and rest after exercise.

It seems that I am making excuses for not exercising. But in my heart, for most people I met, I don't recommand them to exercise. Still, exercise cost energy and time, and may end up in no gain.

I know many people, especially brainer worker like my professor and teacher, who never exercise, still in good health state and live to 90s. This makes me further question the role of exercise in our life.

### For those who want to exercise

For those want to strengthen their body, have the will to keep exercise for life time, and have much time for exercising, I still have some advice for you, as an experienced person:
- Keep exercising. Just keep it, without break. If it rains, you can exercise indoor. If you hurt your leg, you can exercise your arm. Persistence is the most important and also the most difficult part of exercising. 
- Not exercising too much. Though there is no evidence that exercising can extend our life span, but it is known that exercising too much will accelerating our body aging, even hurt your body.
- Exercising with a friend or group, if possible. Others company helps you go further.
- Buy some professional sports equipment if affordable. They will help you exercise more scientifically and effectively, and make you more confident.

The benefits of exercise are very obvious:
- Strengthen your body.
- Build your body and make you attractive.
- Make you feel confident in doing everything.


#### Tips for exercising:
- Exercise in the morning and night are both okay, depending on your personal habits.
- You can exercise in the morning with or withour breakfast. Without breakfast, you can lose weight more easily. Aerobic exercise on a empty stomach is the most effective way to reduce fat and weight.
- If you exercise at night, at least three hours before bed. Otherwise it may affect your sleep.

**Hope you enjoy exercising!**



## 韩国电竞

今天京东输给T1，感觉英雄联盟这游戏还是韩国人在宰治。
我一直认为中国人是世界上智商最高的民族，甚至不愿意加上之一。这是我根据生活经验和在网络世界和书堆里的见闻所得出的结论。准确来讲是东亚人最聪明，这里的东亚主要包括中国，越南，韩国，日本，等。
有些人问既然你说中国人智商高，那为啥各种科技发明不如欧美发达国家？很简单，因为很多因素对科技发明有较大影响，中国人在科学上的聪明才智其实被限制了，至于怎么被限制的我这里就不说了。很多华裔科学家在欧美国家取得的辉煌成就也能说明这一点。
而对于不受限制，或者收限制比较少的那些领域，中国人一向是很出色的，比如艺术创作（港澳台），比如文学成就。
其实电竞也是一个受限制很少的领域：就是坐在电脑面前，用鼠标和键盘操作，没有文化、政治、思想的约束，没有暗箱操作，纯凭实力。这些年中国电竞的蓬勃发展，出现了像Uzi这样的天才选手，在国际赛场上的亮眼表现，我觉得是理所当然的，中国人就是智商高，有天赋。欧美人打电竞就是不如东亚人。
但韩国电竞事实上比中国电竞厉害，这从过往的成绩中也能看出。
当然韩国电竞产业化程度比中国高是事实，中国孩子都跑去高考也是事实，所以也不能完全说明中国人天赋就不如韩国。韩国每时每刻每十七个人中就有一个在打英雄联盟。跟别说星际争霸和Dota这种韩国统治力更强的游戏了。中国电竞还有很长的路要走。无论是选手自己还是体系。
我依然相信，在中国孩子都能自由选择人生道路之后，在中国家长对电竞有更多的认识后，当中国主流社会价值认可电竞后，中国电竞可能胜过韩国。

## 瘦子和胖子

大部分瘦子瘦的主要原因是基因导致的，胖子也一样。在吃同量食物，保持同样运动量的情况下，瘦的人无非两种情况：1. 他们的消化吸收能力低，吃的东西都流失了 2. 他们的身体消耗高（这里的消耗尚不明确，可能是身体代谢，可能是某些激素分泌，甚至是身体缺陷导致某个机能需要额外能量）

从某些经验来看，一般聪明的人偏瘦，瘦子也一般比较聪明。这一点其实可以在生物进化论上得到推理验证：瘦子的两种情况（消化差和消耗大）在食物有限的原始社会是致命的，能存活下来的瘦子一定是有着独特的长处（比如智商高，可以设计陷阱捕捉猎物），来弥补他们身体上的短板。

当然了，在肥胖率飙升的现代社会，怎么吃都不胖应该是很多人梦寐以求的体质。

## 自慰和做爱的区别

中医认为，手淫（自慰）对身体有严重危害：消耗肾精，引起肾虚，腰酸背痛，精神萎靡。但是西医普遍认为手淫对身体没有直接伤害（但可能会上瘾或者愧疚）。从网上的一些言论和自己的直觉来看，中医的说法可能比较正确（事实上中医对于很多现象的描述都是很准确的，但是往往不能科学系统地解释其背后的原因）。

假设中医的说法是正确的，那么自慰和男女做爱的区别是什么呢？同样是用动用了“肾精”“精气”，为什么偏偏自慰就导致了“亏损”“精神萎靡”？而男女交合之事被中医认为对身体有益。这方面中医的解释是“男女阴阳交合，互相滋补”，但是如何“互相滋补”尚无解释。这两种性行为的本质区别到底在哪里？

我所能想到的可能原因：做爱时双方都是身体接触较多，多感官多部位刺激，全身心的反应。相比之下自慰对身体的刺激比较局限，对于身体的局部刺激导致交感神经的异常。

## 共产主义

马克思认为人区别于动物的最大特点，就是人本质上就需要“劳动”，既"创造性地改造环境”。
原始人打扫自己的山洞，你整理自己的房间...这些工作和劳动都会使我们感到快乐。劳动本来就是一件快乐的事，不然人和死尸没有区别。

这也是马克思的牛逼之处，理论精髓之一一人的本质就是需要工作、热爱工作的，工作是人之所以为“人”的重要组成部分。
但是，资本主义世界的雇佣关系，将工作这个部分严重扭曲了——你的工作和劳动不再直接使你感到快乐，获得改造世界的成就感。你的劳动成果被资本家获取，你得到的只是钞票，然后再使用钞票去获取其他形式的快感。资本主义的这一过程将劳动和劳动本身给人的快乐分开了。以至于将“劳动”与“人性”剥离开来。
如果你在你的工作中感觉不到劳动和创造的乐趣，为的只是资本家支付的雇佣金，那么你已经被资本主义异化了。

而这种现象在现在的社会中相当普遍。这是人性被剥离的悲哀。很多人付出了大量的劳动，却没有获得相应的劳动成果和劳动的快感，最终厌恶劳动，认为劳动是违背人性的。大部分人都是被资本异化的，人们普遍认为，工作和劳动是受罪，下班才是人生的开始。

如果现在有人说自己“热爱劳动”，大家大概率会对这个人嗤之以鼻。

马克思对这种现象感到悲哀，于是提出了共产主义：各尽所能，各取所需。每个人劳动的目的都是“创造性地改变环境”，“各取所需”将劳动成果直接作用于自身。这是一个朴素的良性循环，劳动-成果-快感-劳动。

这样的社会理论上是可以维持下去的，而且只会越来越好。
但是如何“跳跃”到这样的理想社会呢？
大部分人抱有悲观的想法：我们无法过渡到这样的理想社会。我曾经也是个minimalist, 心想现在的社会已经是被资本异化了，想让大家集体性地变得各尽所能，无私奉献，这似乎是件不可能的事。

直到我进入了互联网这个大家庭。
在互联网上, github, stackobverflow, 各种汉化组和免费的开源软件...这些都是互联网上来自世界各地的善良美好的人们所创建的，而且几乎是完全的无私奉献。这些互联网上的资源，不仅领域广泛，而且数量巨大。可以说，互联网上已经产生了无数个共产主义社区。

我坚信，在未来信息继续爆炸、信息公开度越来越高的某个时间点，互联网会成为共产主义的沃土，最终培育出真正的共产主义。