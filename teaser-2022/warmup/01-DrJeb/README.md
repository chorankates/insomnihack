# [01 - DrJeb](https://teaser.insomnihack.ch/challenges/chall6/solvers)

## description
> Dr. Jeb was able to analyze the virus in depth. He believes in the power of open source so his disassembler is publicly available here.
> It's time to check his research with practice.

### links

  * [dissaembler](https://github.com/doctor-jebaited/research)
  * [practice](https://static.insomnihack.ch/media/VirusINC-2f2decd2db45ea7368eeab89d0134afce30254f7f7f4e6a0d6d5e7ff91618569.png)

## walkthrough

cloned the repo, ran as specified:
```
$ python VirusDisass¹É®ÐZ#Ä¹É®Ð./ÄÉrusINC-2f2decd2db45ea7368eeab89d0134afce30254f7f7f4e6a0d6d5e7ff91618569.png
JÈu)¯$æ¶:fc¨³#[}¥ôözùÄl¥ä­1ù(=\ÌÌkÄà\ £¨ õà
                                                         4¤
àêgMÓQ¡T½1X'5V'jAÙâôaÍ0ÉÑ
                 P^	{
                      ]H¾Ò_»àI@¨g2$ÜPÒÐW)X*dÑ§LÀr@ÊÔ[                     Ï Ï	)^¯x6&%ÆÞG­­~Xµbã  ÿ Í 	±xè8íô±0èníôzGÐkù¿@/Ð·²¿M(×·ìY  þóì
                                                                ÆÇÆÇ´ÒÇÒûïû^xQ=SLÁä»øÁG§¥ÄÚÓþ?ë¹                                      SÆß=   Æß=
                                         Côôõ©©ïèèÙr$ññÞÞÛ¤¤ªl¤¤                                  :J	y
5 ©|´´gk=>¤¤ò®ÐÐ¨õ&ÁÁð÷üüµÔÉ¥¥ààñDX  I)ÜÜ
º
ºnt|¡9tø{¥:Ë¸`Zúí=Piwiø÷ñ½R¥ê´ø»¯Èr*CsÕ
    ¡  ø ¥ Ë¸  úí     ø÷ñ½ ¥ê´ø»¯È    ÕÔbøùÿd¸Ñ7ÕÌæ±
    |28èè)Á0Aò­cú³fd³´#Ý´¼æþ¼þÆ(ù£¢í£¢úàÙú;àÙÊïÅ»·ïç»·ìç¡¥ìññ±¶ÔU·Ù6 a=Âvò Â ò
j}««
                                                                                           ¬¼­9u`©·ª       C£¡bçl
¸0
qÊÛ©q¡gNíÜ4æ       Í¯Ë(ô	È%Æ#!PÌ+÷ÓG/¡Áó÷Fm%k²o0Çßö;oãcs£ÄÎEÜ92Ù+ün­)¾¶¦Vu   ¹:»Õ2PAí
Ù¬¼'À÷Ö«pi­æëýí×~¿÷ì?Gtî%Â<·¨Ô~[íì£ÿ²^Nï¹o¬±zäÞ·ð?ÿâûÂòàÿ_ëüçì
 ÊÛ  © ¡  íÜ æ      ¤ÀÓ ¸   ÊÕ ¡  ²      [£pn ô  Á      È Æ   Ì ÷Ó  ¡Áó÷    ² ù ÈÇ °ã-7ë­Æ%uÇßö  ã  £ÄÎ Ü  Ù ü ­ ¾¶¦     ¹ »Õ   í
Ù¬¼ À÷Ö«  ­æëýí× ¿÷ìã?gîýÂö·¨ÔçØíì£ÿ²Û#ï¹ £± äÞ·ð ÿâû  ©  ´ ¯   ÏÑõ Âòàÿ ëüçì ôò¿÷Êñ ºÅ ë      Õ3~
Qæ,eÐJIXI·l%EºÕN³]H ã  Ìý ö¹Ç çØó¿ Î½Û åè                                                    ñ  Ãñ   ð  âðÜ                    °    ë    ì
 æ  Ð    ·   ºÕ ³                                                                                                                           Õ
```

ok, that's not right.

looking at requirements.txt,
```
$ cat requirement.txt
numpy
# My years of research are contained in this doctorsecret package
git+https://github.com/doctor-jebaited/secret1234.git@f464e6774efe95ff3fc0fdf7464659240cfff09f
```
ok, let's look at that repo

in commit [https://github.com/doctor-jebaited/secret1234/commit/f464e6774efe95ff3fc0fdf7464659240cfff09f](https://github.com/doctor-jebaited/secret1234/commit/f464e6774efe95ff3fc0fdf7464659240cfff09f), `SECRET = 75`

however, [https://github.com/doctor-jebaited/secret1234/commit/c83ec60a5235e5012c80e6e2fc8c1eaff22b5372](https://github.com/doctor-jebaited/secret1234/commit/c83ec60a5235e5012c80e6e2fc8c1eaff22b5372) changed it to `SECRET = 133`

plugging that in to `VirusDissambler.py` get us:
```
$ python VirusDisassembler.py ../VirusINC-2f2decd2db45ea7368eeab89d0134afce30254f7f7f4e6a0d6d5e7ff91618569.png
ATAATGATAATCGATGTTTATGCGCCTGCGGATCATAACTAAAATAAATTCTCAAAAGTACAACGGGTTTCGCGGCGAAGGATTACACACACGGATGGTGGCCGAGCGGTTTATAGTTATTTTCCCATCGGGGATACGTCCGAAATTCATCACTGAGGGGAGTCTCTCAGTCCACCGGACGTCAAGATCGCAGGTGGCTCAGACTACGAGGGTGTCGTTCATGGGTGGAGCCTGTTCGTCTGACCTTAGGCTGTGACTCAGCAAGACATGGTCTCGAGTTCGTCGTTCAGTAGGCGAGGGGCINS{W3LCOME_2o22_1NS0_B3_Car3fuL}GGAAAGTAAGACGTCAGTGTCCTTCTGCTTAGCTCCTAAGGTATGCCGTCTGTTAGTATGTTGCAGAGACTGACTCCGAGAACATCACGATATTCTTGACTATGCGAAAGTGAAGCGACACCTCGGATGGATTCCAGGACTCCGTATTTCCACGTGAAGACCATTGAGAGCGGGGTTCATTGAGAGTGAGGAGGTCTCAAAACGGTGTAATTTAACGACACTGATTGATTTCCGAGCCTCTGAGTGCCAACGACTACATTTTAAGTCCCATGACATCGGACCGAAATGTACGTCCCTCCAAT
```

and that's a flag.

## flag
```
INS{W3LCOME_2o22_1NS0_B3_Car3fuL}
```
