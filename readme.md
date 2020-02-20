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

<h2 align="center">Introduction</h2>

Sina Weibo is Chinese largest public social media platform. 
The latest and most popular social events will be disclosed and discussed on Weibo as soon as possible.
Therefore, it is of great significance to build a real-time and full-scale Weibo public opinion dataset.

At present, given specified keywords and a specified period, there are two kinds of methods for
constructing Weibo tweet datasets: (1) Applying advanced search API given by Weibo; (2) Traversing all Weibo users, collecting all their tweets in
the specified period, and then filtering tweets with specified keywords.

However, for the first kinds of method, due to
the limitation of the Weibo search API, the result of
one time search contains up to 1000 tweets, making it difficult to build large-scale datasets. As
for the second kinds of method, although we could
build large-scale datasets with almost no omissions,
traversing all billions of Weibo users requires very
long time and large bandwidth resources. 
In addition, a large number of Weibo users are inactive,
and it makes no sense to traverse their homepages,
because they may not post any tweets in the specified period.

![](./images/dataset-builder.png)

To alleviate these limitations, we propose a novel
method to construct Weibo tweet datasets, which
can build large-scale datasets with high construction efficiency. Specifically, we first build and dynamically maintain a high-quilty Weibo active user
pool (just a small part of all users), and then we
only traverse these users and collect all their tweets
with specified keywords in the specified period.

<h2 align="center">Weibo Active User Pool</h2>
Based on init seed users and continuous expansion through social relationships, 
we first build a Weibo user pool including more than 250 million users.
The active Weibo user pool is constructed based on Weibo user pool and follow 4 rules:

|Item|Rule|Item|Rule|
|:---:|:---:|:---:|:---:|
|Follows number| \> 50 |Tweets number| \> 50 |
|Fans number| \> 50 |Recent post| \< 30 days |

Finally, we build a Weibo active user pool with **20 million** users, accounting for 8\% of the total number of weibo users.

<h2 align="center">Weibo Public Opinion Datasets</h2>

⚠️**Note that the following datasets all have been desensitized**

### COVID-19

Paper: [Weibo-COV: A Large-Scale COVID-19 Social Media Dataset from Weibo](https://arxiv.org/abs/2005.09174)

- Time Period: 2019-12-01 00:00 - 2020-04-30 23:59 (GMT+8)
- Keyowds: [totle of 179 selected keywords](./keywords/COVID-19.txt)
- Amount: 
40,893,953 tweets filter from 692,792,816 original tweets by keywords. 
In addition, we also release all original tweets with GEO tag without keywords filtering, covering 45,902,071 tweets.
- Date Format : [The description of fields](https://github.com/nghuyong/WeiboSpider/blob/master/.github/data_stracture.md#%E5%BE%AE%E5%8D%9A%E6%95%B0%E6%8D%AE)
```csv
_id,crawl_time,created_at,like_num,repost_num,comment_num,content,origin_weibo,location_map_info
IBddo6Ee8,1587524917,2020-04-01 00:00,0,0,0,【#印度返乡人员被用水枪消杀# 长途步行回家20多人死在路上】3月30日，印度北方邦工作人员用水枪对返乡工人进行“消杀”。据媒体报道，这些人在德里等地打工。3月24日，印度宣布全国封锁21天。工人们没有了收入，因此选择回到家乡，但所有交通工具已停运，数百万人只能走路回家。#聚焦新冠肺炎疫情#@新京报我们视频 http://t.cn/A6ZSra22转发理由:转发微博,IBb2q8ghj,
IBddIwsjJ,1587873452,2020-04-01 00:00,0,0,0,【纽约州长科莫再次发出求助信号：请大家都来帮帮忙吧！】当地时间3月31日，纽约州州长安德鲁•科莫再次发出求助信号，请求全国的医护人员来支援纽约州抗击新冠肺炎。他表示其他州的疫情有可能也会和纽约州一样严重，现在帮助纽约就是帮自己。这是同舟共济的时刻啊！据悉，目前只有亚特兰大市的数十名医护人员准备前来援助纽约抗击新冠肺炎疫情。#纽约州州长感谢中国捐赠1000台呼吸机#（视频：一侨 编辑：世东） http://t.cn/A6ZoEAEF转发理由:转发微博,IBcwKmamg,
IBddsgrW8,1587585761,2020-04-01 00:00,0,0,0,日本人气编剧、演员#宫藤官九郎#确诊新冠肺炎！ 转发理由:………？？？宫九？？[失望],IBcb6ejVk,
IBddu1G7S,1587531260,2020-04-01 00:00,1,0,0,#乔木美国疫情日记#  你有一个美国梦吗？你想了解真实的美国吗？你还在听什么房东和K驴瞎吹牛逼吗？骚年，李爷我给你推荐一下@乔木DC ，著名的北外乔木。想当年，为了追求自由呼吸香甜的空气，去国怀乡不远万里到了美国。现如今，为了尽可能给你一个真实的疫情下的美国，乔木开始了他的#乔木美国疫情日记# ，在他的日记里，一不开篇说今天天气怎么了，二不听医生朋友说，三不叫撞天屈（不公、黑幕、极左）。乔木直奔主题，以自己的所见所闻，描述美国人看病的艰辛和工作的不易。转发理由://@踏遍天山:乔老师危险了——国内写日记的“汪主席”只是被“极左”网上攻击，而美国前面有个写日记的蓝蓝已经“意外”死于车祸——“出门被车撞死”在美国是真实的[黑线],IB1cMdj3B,
IBddw8jIx,1587534313,2020-04-01 00:00,0,0,0,【#你好，明天#】高考确定延期，备战的日子又“充值”一个月。从忧心“翻车”到立志“翻盘”，不少人五味杂陈。但请相信，时间不会辜负每一分努力，梦想不会怠慢每一个脚印。对考生而言，因为疫情见证了历史，更因为坚持参与着历史。健康和公平，一个都不能落下；现在和未来，每一个都要抓在手中。 转发理由:[加油],IBd4FplhX,
IBddHC95C,1587537502,2020-04-01 00:00,0,0,0,"在日前的白宫新冠病毒疫情资讯会上，川普的演讲意味着全球化的结束；美国未来将独立于全球供应链之外，逐步成为一个自给自足的国家。他说到：  ""我们永远不应该依赖外国为我们自己的生存手段... 这场危机是凸显了强大的国界和繁荣的制造业的重要性 ... 过去三年，我们建立了完善的移民系统，并把制造业带回了美国。现在，两党必须团结起来，把美国建设成为一个全面独立的、繁荣的国家：能源独立，制造业独立，经济独立，国界主权独立。美国永远不会成为一个依赖国，将成为一个自豪、独立、自强的国家。美国将推进商务，但不会依赖任何人...""  自2018年以来，市场一直在担心全球供应链的瓦解，和全球化的倒退。这次疫情暴露了全球化最大的弱点：只要全球供应链上任何一个环节告急，就会火烧连营。全球化的倒退，将衍生出一系列的问题。比如，还没有发展起来的新兴市场国家未来的发展的局限；已有的、为满足出口需求投资的产能；以及过去二十年全球化带来的对于通胀的压抑；全球美元流动性的供给，等等。毕竟，二战以来，“和美国搞好关系的国家都富起来了”。  现在，市场面对的是缓缓落下的帷幕，而非升起的序幕。  洪灝，CFA  http://t.cn/A6ZS5n33转发理由:孤立主义回潮",IBa7lgooc,
```
- Download:
If you want to acquire the corpus. Please fill the [application form](https://raw.githubusercontent.com/nghuyong/weibo-public-opinion-datasets/master/.github/Weibo_COV_Application_Form.pdf) and send to Yong Hu (huyong@bit.edu.cn) and Anfan Chen(caf16@ustc.edu.cn).

- Cite this dataset
```
@misc{hu2020weibocov,
    title={Weibo-COV: A Large-Scale COVID-19 Social Media Dataset from Weibo},
    author={Yong Hu and Heyan Huang and Anfan Chen and Xian-Ling Mao},
    year={2020},
    eprint={2005.09174},
    archivePrefix={arXiv},
    primaryClass={cs.SI}
}
```

<h2 align="center">Citation</h2>

If you use this work in a scientific publication, I would appreciate that you can also cite the following BibTex entry:

```
@misc{nghuyong2020@weibo-public-opinion-dataset,
  title={weibo-public-opinion-dataset},
  author={Yong Hu},
  howpublished={\url{https://github.com/nghuyong/weibo-public-opinion-dataset}},
  year={2020}
}
```