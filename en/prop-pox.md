---
title: "Prop Pox"
description: ""
published: true
date: '2019-08-09T09:43:28Z'
tags: ["Bugs"]
editor: markdown
dateCreated: '2009-03-26T21:34:41Z'
---

<figure>
<img src="/_files/images/industryez4.jpg" title="A city affected by prop pox; note the similiarity to the city on low graphics settings." width="250" />
<figcaption>A city affected by prop pox; note the similiarity to the city on low graphics settings.</figcaption>
</figure>

**Prop pox** is the name given to a problem affecting [SimCity 4's](/simcity-4) Save Games, which causes props to gradually disappear from city tiles. The first submissions of such problems where posted in late April/early May by , and . After the series of tests, community member , posted an explanation of the problem on [SC4D's](/simcity-4-devotion) forums.

### Early tests (2007-early 2009)

After the first alarming comments about the problem were posted, immediately tests to find the cause of prop pox were initiated by different members of the community. What was learned in that period of time can be summarised into the following seven points:

- The prop pox is most definitely not a graphical bug, thus it can't be resolved by just tweaking the graphical settings of the game, nor the graphic card.
- It isn't some kind of computer issue or software conflict. Defragmenting the disc and increasing the virtual memory has no effect in resolving the problem.
- The problem isn't exclusive to one computer system. It can affect games running on machines with Windows 2000, XP, Vista or even Macintosh.
- Hardware settings are not responsible for the prop pox, as it can affect games running on all kinds of processors, sound & graphic cards, etc.
- Occurrences of the problem are mostly limited to use of the big (4km x 4km) tiles. It's not a matter of population, traffic or density, however.
- The problem lies in the city's save file. It has been noted that the save files affected by prop pox, shrink by 200 to 400kb, then during subsequent saves, continue to shrink further in size. As it was discovered that props are stored in the subfile of type 2977aa47 (also known as the network subfile), which usually grows with every save, it would be logical if that subfile shrinks, that the entire save file would shrink in size also. Thus, it would appear clear that these 200 to 400kb of data are [props](/prop) which are being lost in the process of saving.
- It was speculated that a memory overflow somewhere could be corrupting the save file. Two possible explanations where published, one suggesting that the EP1 update program was the cause (this has been thoroughly de-bunked ). Another potential cause was the use of multiple copies of props using the same IDs (otherwise called prop overrides).

### New Revelations (2009)

On the 24th of February, posted a very detailed and easy to understand analysis of the problem. Based on what we already knew, along with much testing and observations, he came to the conclusion that the cause of the issue was the use of modified versions of original, in-game [Maxis](/maxis)' props. This theory has been called 'prop theory', and is known largely known as the most probable one. During testing, only two files were identified as causing the issue, BSC MEGA Props Misc Vol02, which was swiftly patched by in 2009. The other identified file was PEG-OWW2_BDK_RESOURCE.dat by . The explicit problem was identified as changing an existing standard prop to a timed prop, technically switching between RTK1 and RTK4 types.

It is possible to prevent the cause of Prop Pox and use the BDK file, which is a dependency for 2 further CDK3-OWW2 packages. This requires modifying the Props using [Ilive's Reader](/reader), instructions can be found in [this post](http://sc4devotion.com/forums/index.php?topic=7066.msg224892#msg224892). However, the affected file was never patched on the exchanges, so those not wishing to fix the file, are advised not to use it.

It's important to note, Prop Pox is a devastating problem. Unlike most such issues, there is almost no way to restore any affected files. This is because if a file that causes Prop Pox exists at any time in your Plugins folder and you save the city, that single action will plant the seeds of the problem. Due to some rather technical details regarding the way save data is handled, the effects of Prop Pox will only occur if the 2977aa47 subfile expands beyond a certain size. If this never occurs, the issue will remain dormant and you will simply never run into problems. However, if it does expand, the data format is changed, at this point errors in the prop data will lead to cascading incorrect data writes from then on. It's these operations that continue to wipe out ever more props, with each subsequent save. What's more, even if you have backups of your cities to restore them to working order, those files will still contain the "trigger", as such they will ultimately be consigned to the same fate eventually.

Despite those findings, however, the discussion continues, as the 'prop theory' can't be considered definitive, however it is the most probable answer we have so far.

### Hope for Prop Poxed Cities/Regions (2018)

Fast forward to 2018 and , creator of SC4Fix, which solved the Puzzle Piece over Transit Enabled CTD problem, decided to take a look at Prop Pox. His conclusion of the cause: "The main change in PEG's exemplar is that the Nighttime State Change entry (one byte large) in the Maxis exemplar was replaced by a Prop Time of Day entry (two Float32s, or eight bytes large)." What is interesting about this is that another user, , came to a similar conclusion in 2015, see post here <http://sc4devotion.com/forums/index.php?topic=7066.msg491621#msg491621>.

Simmaster07 however was able to test new code, using his .dll injection method and at first glance it would appear a fix for Prop Pox has finally arrived. Some caution should be heeded before rushing to install it, since right now it is not clear why the changes fix the Prop Pox problem. Given that altering how the game saves data is a pretty big deal, until sufficient testing and feedback can be gathered, we shouldn't assume anything.

What we do know however, if you have a Prop Poxed city or region, this fix appears to solve the problem. Since such cities until now we're pretty much useless, there is no real risk with using this fix, literally you have nothing to loose. Similarly, all the results thus far completely suggest with this fix installed, Prop Pox will not occur. As usual, it is recommended to keep regular backups of your regions, but especially so when using relatively untested fixes like this.

Hopefully though, we do now have a way of preventing and curing this issue once and for all. These developments are very promising and the potential benefits should not be underestimated.

### Controversies

Following the publication of bap's explanation of the prop pox, numerous controversies among several community members occurred, including Pegasus himself. On [SimPeg](/simpeg), he had written a post regarding bap's results and more generally that of prop pox itself. During which he expressed a very sceptical point of view towards both, stating that in his opinion there was no evidence to support 'prop theory' as true or caused by the BDK file.

## Other

- [What causes prop pox, and how to prevent it](http://sc4devotion.com/forums/index.php?topic=7066.0) by ([SC4D](/sc4d))
- [The Prop Pox!](http://sc4devotion.com/forums/index.php?topic=1201.0) by ([SC4D](/sc4d))
- [Prop Pox?](http://simpeg.com/forum/index.php?topic=7276.0) by ([SimPeg](/simpeg))
- [Revisiting Prop Pox and Prop Theory](https://community.simtropolis.com/forums/topic/74667-revisiting-prop-pox-and-prop-theory/) by ([ST](/st))
- [SC4 Fix Download](https://community.simtropolis.com/files/file/30883-sc4fix-third-party-patches-for-sc4/) ([STEX](/stex))
- [SC4 Fix Source Code](https://github.com/nsgomez/sc4fix) (GitHub)

> **Note:** This article needs expanding.
