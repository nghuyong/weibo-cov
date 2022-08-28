<h1 align="center">weibo-public-opinion-datasets</h1>

<p align="center">Continuously updated Sina Weibo Public Opinion Datasets (only for research)</p>

<p align="center">
  <a href="https://github.com/nghuyong/weibo-public-opinion-datasets/stargazers">
    <img src="https://img.shields.io/github/stars/nghuyong/weibo-public-opinion-datasets.svg?colorA=orange&colorB=orange&logo=github"
         alt="GitHub stars">
  </a>
  <a href="https://github.com/nghuyong/weibo-public-opinion-datasets/issues">
        <img src="https://img.shields.io/github/issues/nghuyong/weibo-public-opinion-datasets.svg"
             alt="GitHub issues">
  </a>
  <a href="https://github.com/nghuyong/weibo-public-opinion-datasets/">
        <img src="https://img.shields.io/github/last-commit/nghuyong/weibo-public-opinion-datasets.svg">
  </a>
  <a href="https://github.com/nghuyong/weibo-public-opinion-datasets/blob/master/LICENSE">
        <img src="https://img.shields.io/github/license/nghuyong/weibo-public-opinion-datasets"
             alt="GitHub license">
  </a>
</p>


**The end-to-end research service platform [yisukeyan.com](https://yisukeyan.com/) has been launched!! Feel free to contact us!👏👏👏**

<h2 align="center">Introduction</h2>

Sina Weibo is the largest Chinese public social media platform. The latest and most popular social events will be disclosed and discussed on Weibo as soon as possible. Therefore, it is of great significance to build a real-time and full-scale Weibo public opinion dataset.

At present, given specified keywords and a specified period, there are two kinds of methods for constructing Weibo tweet datasets: (1) Applying advanced search API given by Weibo; (2) Traversing all Weibo users, collecting all their tweets in the specified period, and then filtering tweets with specified keywords.

However, for the first kinds of method, due to the limitation of the Weibo search API, the result of one time search contains up to 1000 tweets, making it difficult to build large-scale datasets. As for the second kinds of method, although we could build large-scale datasets with almost no omissions,
traversing all billions of Weibo users requires very long time and large bandwidth resources.  In addition, a large number of Weibo users are inactive,
and it makes no sense to traverse their homepages, because they may not post any tweets in the specified period.

![](./images/dataset-builder.png)

To alleviate these limitations, we propose a novel method to construct Weibo tweet datasets, which can build large-scale datasets with high construction efficiency. Specifically, we first build and dynamically maintain a high-quilty Weibo active user pool (just a small part of all users), and then we
only traverse these users and collect all their tweets with specified keywords in the specified period.

<h2 align="center">Weibo Active User Pool</h2>
Based on init seed users and continuous expansion through social relationships, we first build a Weibo user pool including more than 250 million users.
The active Weibo user pool is constructed based on Weibo user pool and follow 4 rules:

|Item|Rule|Item|Rule|
|:---:|:---:|:---:|:---:|
|Follows number| \> 50 |Tweets number| \> 50 |
|Fans number| \> 50 |Recent post| \< 30 days |

Finally, we build a Weibo active user pool with **20 million** users, accounting for 8\% of the total number of weibo users.

<h2 align="center">Weibo Public Opinion Datasets</h2>

⚠️**Note that the following datasets all have been desensitized**

### Weibo-COV
Paper: [Weibo-COV: A Large-Scale COVID-19 Social Media Dataset from Weibo](https://arxiv.org/abs/2005.09174)

#### News
**[UPDATE-2021-01-18]** We released **Weibo-COV V2**, including 20 million Weibo active user pool!

**[UPDATE-2020-12-30]** We have received over **130** applications from all over the word!!
 Weibo-COV has supported more than **30** publications and more than **100** programs! 
 **Weibo-COV V2** is coming soon!! If you have some advices, feel free to email me!

**[UPDATE-2020-10-06]** Our paper about this dataset has been accepted by [the 1st Workshop on NLP for COVID-19 (Part 2) at EMNLP2020](https://www.nlpcovid19workshop.org/emnlp2020/).

**[UPDATE-2020-06-24]** Add the field of `user_id` to identify each user. 
To respect privacy, the released `user_id` is the **hashed result** of the origin Weibo `user_id`.

#### Weibo-COV V2
Compared with Weibo-COV, Weibo-COV V2 has **longer time span**, **bigger data size** and **more refined keyword filtering method**. 
We also released **20 million Weibo active user pool** after desensitization to promote extensive and in-depth researches.

- Time Period: 2019-12-01 00:00 - 2020-12-30 23:59 (GMT+8)
- [Keywords](./keywords/Weibo-COV-V2.txt): Common keywords and monthly different keywords. For one month, we use common keywords and this month's specific keywords to filter this month's all original tweets. 
- Amount: **65,175,112** tweets filtered from **2,615,185,101** original tweets by keywords.
- Sample: Weibo-COV V2
```csv
_id,user_id,crawl_time,created_at,like_num,repost_num,comment_num,content,origin_weibo,geo_info
Jwm2cyhQQ,e0470a66f95fe66d,1607931932,2020-12-01 00:00,0,0,0,【抗疫路上，#幕后的科研专家走了#】疫苗攻关争分夺秒，他总想再快点！因连续工作、过度劳累，中国医学科学院病原生物学研究所研究员赵振东教授倒在了出差途中，最终抢救无效，于9月17日在北京不幸逝世，享年53周岁。赵振东教授是我国从事病原生物学和感染免疫学研究的知名专家，疫情伊始，他说：“这...全文转发理由:[泪],Jwl894jgH,
Jwm2ld0aZ,8034accc2f9b93ae,1607986175,2020-12-01 00:00,0,0,0,【蒙古羊肉运抵武大中南医院，#雷神山医护工作者吃上蒙古羊# 】经过检验、隔离等程序， 当日中午，一辆载满蒙古羊肉的货柜车从武汉阳逻港运到武汉大学中南医院 。货车开箱后，工作人员立即完成抽检，再由后勤保障部的工作人员运送至医院食堂，羊肉将分发给医院一线医务人员。致敬这些曾奋斗在雷神山的...全文转发理由://@午后狂睡:………馋了,JwlnBBw1c,
Jwm2gs8h0,2079268f5b85f1a8,1608006715,2020-12-01 00:00,0,0,0,😷疫情对企业而言，是一个加速淘汰和加速升级的过程，而往往最能存活下来发展的是那些最能适应环境变化的。12XEdaN01。�社群团购的商业模式，完美契合经济发展脚步，是最能完美承接原有行业属性且继承发展！,,
Jwm2eDupl,8af7d9c40104eecd,1608046707,2020-12-01 00:00,0,0,0,@湖南卫视 ❓贵台今晚综艺上愚蠢的提问和无知的tag出自何处，是导演的错，还是贵台因为疫情已经可以不关注自己艺人行程及作品，甚至，可以为所欲为了呢？  1️⃣ 蔡/程/昱自18年起参加贵台srrx第一季 并成为‼️年度首席歌手之一‼️节目结束后签约为你家演艺事业部艺人，做了贵台的打工仔，兢兢业业，...全文转发理由:@湖南卫视 [微笑],JwlJrftvi,
Jwm2cAuxG,03002291162f3d23,1608113760,2020-12-01 00:00,0,0,0,今年因为疫情，很多台湾歌手都留在对岸参加那边的跨年演唱会！一时之间，台湾各地的跨年阵容重回了十年前群星云集的画面！比如台北跨年场，就会集齐伍佰、魚丁糸、田馥甄、林宥嘉、萧敬腾、艾怡良、宇宙人等等音乐人，比近年的阵容夸张很多！！  这个阵容还在公布中，估计到12月月底才有完整的模样，届...全文转发理由:现在游去对岸还来得及吗,Jwlcrf9Lz,
Jwm2zp42u,46d455bafebcb289,1608125947,2020-12-01 00:00,0,0,0,希望2020年的12月一切都顺顺利利的呀！ 2020年的前半年与下半年 是我人生很重要的转折点 迄今，仍然会很怀念疫情在家的日子 那是我自上学来 在家最久的日子 你好！12月,,
```
- Sample: 20 million Weibo active user pool
```csv
user_id,gender,province,city,birthday,fans_num,vip_level,crawl_time
6e8c581b932a9d4e,女,北京,,0001-00-00,199182410,6级,1576187979
f53557f7d61027bc,女,北京,海淀区,0001-00-00,185217690,7级,1576148765
2036a1474ebcc02c,女,北京,海淀区,01-01,183843761,6级,1576085666
a98d14fb1231482b,女,北京,,1984-10-15,159145854,6级,1575999468
2102b3df71b308c6,女,北京,海淀区,0001-00-00,125274267,7级,1576189968
```
- Download:
If you want to acquire the corpus. Please fill the [application form](https://raw.githubusercontent.com/nghuyong/weibo-public-opinion-datasets/master/.github/Weibo_COV_V2_Application_Form.pdf) and send to Yong Hu (nghuyong@163.com) and Anfan Chen(caf16@ustc.edu.cn).


#### Weibo-COV
- Time Period: 2019-12-01 00:00 - 2020-04-30 23:59 (GMT+8)
- [Keywords](./keywords/Weibo-COV.txt): totle of 179 selected keywords
- Amount: 
40,893,832 tweets filtered from 692,792,816 original tweets by keywords. 
In addition, we also release all original tweets with GEO tag without keywords filtering, covering 45,901,994 tweets.
- Sample:
```csv
_id,user_id,crawl_time,created_at,like_num,repost_num,comment_num,content,origin_weibo,geo_info
IBddo6Ee8,96e7c5482014ffbb,1587524917,2020-04-01 00:00,0,0,0,【#印度返乡人员被用水枪消杀# 长途步行回家20多人死在路上】3月30日，印度北方邦工作人员用水枪对返乡工人进行“消杀”。据媒体报道，这些人在德里等地打工。3月24日，印度宣布全国封锁21天。工人们没有了收入，因此选择回到家乡，但所有交通工具已停运，数百万人只能走路回家。#聚焦新冠肺炎疫情#@新京报我们视频 http://t.cn/A6ZSra22转发理由:转发微博,IBb2q8ghj,
IBddIwsjJ,40a4b94891260d41,1590476339,2020-04-01 00:00,0,0,0,【纽约州长科莫再次发出求助信号：请大家都来帮帮忙吧！】当地时间3月31日，纽约州州长安德鲁•科莫再次发出求助信号，请求全国的医护人员来支援纽约州抗击新冠肺炎。他表示其他州的疫情有可能也会和纽约州一样严重，现在帮助纽约就是帮自己。这是同舟共济的时刻啊！据悉，目前只有亚特兰大市的数十名医护人员准备前来援助纽约抗击新冠肺炎疫情。#纽约州州长感谢中国捐赠1000台呼吸机#（视频：一侨 编辑：世东） http://t.cn/A6ZoEAEF转发理由:转发微博,IBcwKmamg,
IBddsgrW8,bbb2f1be4131dde7,1587585761,2020-04-01 00:00,0,0,0,日本人气编剧、演员#宫藤官九郎#确诊新冠肺炎！ 转发理由:………？？？宫九？？[失望],IBcb6ejVk,
IBddu1G7S,3bf1604511aee5dd,1587531260,2020-04-01 00:00,1,0,0,#乔木美国疫情日记#  你有一个美国梦吗？你想了解真实的美国吗？你还在听什么房东和K驴瞎吹牛逼吗？骚年，李爷我给你推荐一下@乔木DC ，著名的北外乔木。想当年，为了追求自由呼吸香甜的空气，去国怀乡不远万里到了美国。现如今，为了尽可能给你一个真实的疫情下的美国，乔木开始了他的#乔木美国疫情日记# ，在他的日记里，一不开篇说今天天气怎么了，二不听医生朋友说，三不叫撞天屈（不公、黑幕、极左）。乔木直奔主题，以自己的所见所闻，描述美国人看病的艰辛和工作的不易。转发理由://@踏遍天山:乔老师危险了——国内写日记的“汪主席”只是被“极左”网上攻击，而美国前面有个写日记的蓝蓝已经“意外”死于车祸——“出门被车撞死”在美国是真实的[黑线],IB1cMdj3B,
IBddFiWg6,dd4a4eac5fa1acdf,1590144952,2020-04-01 00:00,8,1,4,许可馨，苏州人，中国药科大学2019届本科毕业生。公派留学生，目前就读于匹兹堡大学。 李文亮医生垂危之际出口成脏，骂留学生，骂中国人，恨国蛆一枚，怎么就争取到公费资助的呢？ 前有厦门大学田佳良，后有药科大学许可馨，我们的大学怎么就培养出这么多精致的双面人？ 建议药大追加开除，建议取消公费资助，建议追究提供公费资助的机构负责人责任，建议彻查此渣相关联系人背景，净化社会空气。 【补充评论】#留学生许可馨# 的两面人表现值得重视，不可一斥了之，轻轻放过。 此人家境优越，顺风顺水，还托国家的福成了公派留学生，可谓精英家庭成功培养出的精英学子。可是她的内在，却具有鲜明的反社会型人格。 据许可馨的初中同学爆料：许可馨在初中人品就极差无比，成绩很好但是心肠歹毒，随手携带一个小本本，上面都是骂人的话。有网友扒出许可馨的小号，其污浊与下贱更是让人目瞪口呆。 大家是否记得，电影《少年的你》里面有一个名叫魏莱的优等生，面容姣好、目光清澈、成绩出色、人畜无害，实际上却心思毒辣、霸凌同学甚至置人于死地。这种女孩的典型特征是：家境优渥、成绩出色、人人当她们是好学生，其实却是狠毒渣女，极致两面人。 具体到许可馨身上，就是突然呈现另一付嘴脸，对外跪舔，对内鄙夷，其他案例如：洁洁良、杨舒平等。 教育部门必须深刻反省，不能允许诸如此类的反社会人格者利用自己的伪装占尽社会便宜，然后再反噬社会。[组图共11张]转发理由:广大微友虽然有些戾气，言论有些过于犀利，可听着很舒服！ 关于许可馨发表的不当言论，居然也有人给洗白？花钱就可以让一些水军抛弃良心颠倒是非吗？花钱就可以下热搜吗？ 还是说她背后所牵扯的实力够大，罔顾广大微民的愤怒，强行洗白！是否需要一起查查许可馨背后的保护伞了！,IB3OCyTtK,
IBddw8jIx,01c31da0c3b9b553,1590145129,2020-04-01 00:00,0,0,0,【#你好，明天#】高考确定延期，备战的日子又“充值”一个月。从忧心“翻车”到立志“翻盘”，不少人五味杂陈。但请相信，时间不会辜负每一分努力，梦想不会怠慢每一个脚印。对考生而言，因为疫情见证了历史，更因为坚持参与着历史。健康和公平，一个都不能落下；现在和未来，每一个都要抓在手中。 转发理由:[加油],IBd4FplhX,
```
- Download:
If you want to acquire the corpus. Please fill the [application form](https://raw.githubusercontent.com/nghuyong/weibo-public-opinion-datasets/master/.github/Weibo_COV_Application_Form.pdf) and send to Yong Hu (nghuyong@163.com) and Anfan Chen(caf16@ustc.edu.cn).

#### Cite this dataset
If you use Weibo-COV or Weibo-COV V2 in a scientific publication, I would appreciate that you can also cite the following BibTex entry:
```
@inproceedings{hu-etal-2020-weibo,
    title = "{W}eibo-{COV}: A Large-Scale {COVID}-19 Social Media Dataset from {W}eibo",
    author = "Hu, Yong  and
      Huang, Heyan  and
      Chen, Anfan  and
      Mao, Xian-Ling",
    booktitle = "Proceedings of the 1st Workshop on {NLP} for {COVID}-19 (Part 2) at {EMNLP} 2020",
    month = dec,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.nlpcovid19-2.34",
    doi = "10.18653/v1/2020.nlpcovid19-2.34",
}
```
