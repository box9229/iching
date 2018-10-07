

# I Ching Python project

![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/I_Ching_Song_Dynasty_print.jpg/440px-I_Ching_Song_Dynasty_print.jpg)

iching is a packge developed by Cheng-Jun Wang. It employs the method of Shicao prediction to reproduce the prediction of I Ching--the Book of Exchanges. The I Ching ([î tɕíŋ]; Chinese: 易經; pinyin: Yìjīng), also known as the Classic of Changes or Book of Changes in English, is an ancient divination text and the oldest of the Chinese classics.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Yarrow_stalks_for_I_Ching.JPG/440px-Yarrow_stalks_for_I_Ching.JPG)

The Zhou yi provided a guide to cleromancy that used the stalks of the yarrow plant, but it is not known how the yarrow stalks became numbers, or how specific lines were chosen from the line readings. In the hexagrams, broken lines were used as shorthand for the numbers 6 (六) and 8 (八), and solid lines were shorthand for values of 7 (七) and 9 (九). The Great Commentary contains a late classic description of a process where various numerological operations are performed on a bundle of 50 stalks, leaving remainders of 6 to 9.

大衍之數五十，其用四十有九。分而為二以象兩，掛一以象三，揲之以四以象四時，歸奇於扐以象閏。五歲再閏，故再扐而後掛天一，地二;天三，地四;天五，地六;天七，地八;天九，地十天數五，地數五五位相得而各有合，天數二十有五，地數三十，凡天地之數五十有五，此所以成變化而行鬼神也。幹之策二百一十有六，坤之策百四十有四，凡三百六十，當期之日。二篇之策，萬有一千五百二十，當萬物之數也。是故四營而成“易”，十有八變而成卦，八卦。而小成引而伸之，觸類而長之，天下之能事畢矣顯道神德行，是故可與酬酢，可與佑神矣子曰：“知變化之道者，其知神之所為乎“。
# Install
```python
pip install iching
```

# A Quick Tutorial

```python
from iching import iching

def ichingbook(birthday):
    iching.ichingDate(birthday)
    fixPred, changePred   = iching.getPredict()
    iching.plotTransition(6, w = 15)
    guaNames = iching.ichingName(fixPred, changePred) 
    fixText = iching.ichingText(fixPred, iching)
    if changePred:
        changeText = iching.ichingText(changePred, iching)
    else:
        changeText = None
    sepline1 = '\n                    __/\__         '
    sepline2 = '\n                  __|BOOK|__       '
    sepline3 = '\n               ___/_ICHING_\___    '
    sepline4 = '\n                 |-||||||||-|      '
    sepline5 = '\n  _/\___/\___/\__|-|/\/\/\|-|__/\___/\___/\_'
    sepline6 = '\n   ||___||___||__|-||||||||-|__||___||___|| '
    print(guaNames+'\n'+u'本卦: '+fixText+sepline1+sepline2+sepline3+sepline4+sepline5+sepline6+'\n\n\n'+u'变卦: '+changeText)

ichingbook(1985092720180119)
```

# Use

```python
from iching import iching
```

##### 0. Set iching time

```python
iching.ichingDate(1985052620150704) 
# e.g., 19850526 is your birthday and 20150704 is the prediction time.
# of course, your can also input more precise time.
```

##### 1. Start to predict
```python
iching.getPredict()
```

##### 2. Get the iching name
```python
fixPred, changePred   = iching.getPredict()
iching.ichingName(fixPred, changePred  )
```

##### 3. Get the iching text

```python
iching.ichingText(fixPred, iching)
```
	坎卦原文 坎 習坎，有孚，維心亨，行有尚
	象曰：水洊至，習坎君子以常德行，習教事
	白話文解釋 習坎卦：。抓獲俘虜，勸慰安撫他們，通泰途中將得到幫助
	“象辭”說：。
	坎為水，水長流不滯，是坎卦的卦象 君子觀此卦象，從而尊尚德行，取法於細水長流之象，學習教化人民的方法。

“斷易天機”解坎卦坎上坎下，為坎宮本位卦。坎為陷入，陷阱，為險難之境。此時應堅持信心，才能豁然貫通。

北宋易學家邵雍解 艱難危險，重險重陷;事多困阻，謹慎行事得此卦者，運氣不佳，多難危險，事多困阻，宜謹言慎行，退守保安。


##### 4. Understand Three Changes

```python
data = 50 - 1
sky, earth, firstChange, data = iching.getChange(data)
print sky, '\n', earth, '\n',firstChange, '\n', data

sky, earth, secondChange, data = iching.getChange(data)
print sky, '\n', earth, '\n',secondChange, '\n', data

sky, earth, thirdChange, data = iching.getChange(data)
print sky, '\n', earth, '\n',thirdChange, '\n', data
```

##### 5. Plot transitions

```pytnon
%matplotlib inline
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(15, 10),facecolor='white')
plt.subplot(2, 2, 1)
iching.plotTransitionRemainder(1000, w = 50)
plt.subplot(2, 2, 2)
iching.plotTransitionRemainder(1000, w = 50)
plt.subplot(2, 2, 3)
iching.plotTransitionRemainder(1000, w = 50)
plt.subplot(2, 2, 4)
iching.plotTransitionRemainder(1000, w = 50)
```


![](http://7lrzgn.com1.z0.glb.clouddn.com/download.png)


