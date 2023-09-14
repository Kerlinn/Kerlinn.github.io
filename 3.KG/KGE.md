# KGE

**Papers on Knowledge Graph Embedding(KGE)**

# Contents

- [Libraries](#Libraries)
- [Methodologies](#Methodologies)
- [Papers](#Papers)

# Libraries

- LibKGE [code](https://github.com/uma-pi1/kge) 
- OpenKE [code](https://github.com/thunlp/OpenKE) 
- PyKEEN [code](https://github.com/pykeen/pykeen) 
- Pykg2vec [code](https://github.com/Sujit-O/pykg2vec) 
- GraphVite [code](https://github.com/DeepGraphLearning/graphvite) 
- Scikit-KGE [code](https://github.com/mnick/scikit-kge) 
- AmpliGraph [code](https://github.com/Accenture/AmpliGraph)

# Methodologies

## Traditions

### Translation

| Year |  Source   |  Methods   |
| :--: | :-------: | :--------: |
| 2013 |  NeurIPS  |   TransE   |
| 2014 |   AAAI    |   TransH   |
| 2015 |   AAAI    |   TransR   |
| 2015 |    ACL    |   TransD   |
| 2015 |   EMNLP   |  RTransE   |
| 2015 |   EMNLP   |  PTransE   |
| 2015 |   CIKM    |    KG2E    |
| 2016 |   AAAI    |   TransA   |
| 2016 |   AAAI    | TranSparse |
| 2016 |    ACL    |   TransG   |
| 2016 |   IJCAI   | ManifoldE  |
| 2016 |    KR     |  FTransE   |
| 2016 | NAACL-HLT | lppTransE  |
| 2016 | NAACL-HLT |  STransE   |
| 2017 |   AAAI    |  puTransE  |
| 2017 |    ACL    |  ITransF   |
| 2017 |   CIKM    |  CombinE   |
| 2017 |   CIKM    | TransE-RS  |
| 2018 |   AAAI    |   TorusE   |
| 2018 |   AAAI    |  TransAt   |
| 2018 |   EMNLP   |   TransC   |
| 2019 |   KBS*    |    KEC     |
| 2019 |   ICLR    |   RotatE   |
| 2019 |   AAAI    | TransGate  |
| 2019 |   IJCAI   |  TransMS   |
| 2020 |   KBS*    |  ConnectE  |
| 2020 |    IS*    |    MAKR    |
| 2020 |   AAAI    |    HAKE    |
| 2020 |  NeurIPS  |    BoxE    |
| 2020 |    ACL    |    OTE     |
| 2020 |   IJCAI   |  TransRHS  |
| 2020 |   ECAI    |    MDE     |
| 2020 |  COLING   |   AprilE   |
| 2020 |  COLING   |    RatE    |
| 2020 |   CIKM    |  Rotate3D  |
| 2020 |   ICDM    |  LineaRE   |
| 2020 |   ESWC    |  HyperKG   |
| 2021 |   KBS*    |  MRotatE   |
| 2021 |    NC*    | HA-RotatE  |
| 2021 |    ACL    |   PairRE   |
| 2021 |   CIKM    |   CyclE    |
| 2022 |   KBS*    |  ReflectE  |
| 2022 |    NC*    |   DensE    |
| 2022 |    NC*    | StructurE  |

### Geometry

| Year | Source  |  Methods  |
| :--: | :-----: | :-------: |
| 2018 |  AAAI   |  TorusE   |
| 2019 |  ICLR   |  RotatE   |
| 2019 | NeurIPS |   MuRP    |
| 2019 | NeurIPS |   QuatE   |
| 2020 |  AAAI   |   HAKE    |
| 2020 |   ACL   |   ATTH    |
| 2020 | COLING  |   GeomE   |
| 2020 |  CIKM   | Rotate3D  |
| 2020 |  ISWC   |   SpacE   |
| 2020 |  ESWC   |  HyperKG  |
| 2021 |  KBS*   |  MRotatE  |
| 2021 |  KBS*   |  MöbiusE  |
| 2021 |   NC*   | HA-RotatE |
| 2021 |  AAAI   |    5E     |
| 2021 |  AAAI   |   DualE   |
| 2021 |  EMNLP  |   BiQUE   |
| 2021 |  EMNLP  |  FieldE   |
| 2021 |  EMNLP  |    HBE    |
| 2021 |  EMNLP  |   RotL    |
| 2021 |  CIKM   |   GrpKG   |
| 2021 |  CIKM   |   HopfE   |
| 2021 |   WWW   |  MQuadE   |
| 2022 |   NC*   |   DensE   |

### Multiplication

| Year | Source  | Methods  |
| :--: | :-----: | :------: |
| 2011 |  ICML   |  RESCAL  |
| 2015 |  ICLR   | DistMult |
| 2016 |  AAAI   |   HolE   |
| 2016 |  ICML   | ComplEx  |
| 2017 |  ICML   | ANALOGY  |
| 2018 | NeurIPS |  HolEX   |
| 2018 | NeurIPS |  SimplE  |
| 2019 | NeurIPS |  QuatE   |
| 2019 |   ACL   | DihEdral |
| 2019 |  EMNLP  |  TuckER  |
| 2019 |  WSDM   |  CrossE  |
| 2020 |   ACL   |   SEEK   |
| 2020 |  ICML   |  LowFER  |
| 2020 |  EMNLP  |   B-CP   |
| 2020 |  ECAI   |   BTDE   |
| 2020 |  ECAI   |   MEI    |
| 2020 |  ICDE   |  AutoSF  |

### Neural Networks

| Year |  Source   |   Methods    |
| :--: | :-------: | :----------: |
| 2013 |  NeurIPS  |     NTN      |
| 2014 |    KDD    |    ER-MLP    |
| 2017 |   AAAI    |    ProjE     |
| 2018 |   AAAI    |    ConvE     |
| 2018 | NAACL-HLT |    ConvKB    |
| 2018 | NAACL-HLT |    KBGAN     |
| 2018 |   CIKM    |     CACL     |
| 2018 |   CIKM    |     SENN     |
| 2019 |    ACL    |    KBGAT     |
| 2019 |   ICML    |     RSN      |
| 2019 | NAACL-HLT |    CapsE     |
| 2019 | NAACL-HLT |    ConvR     |
| 2020 |   AAAI    |    CoPER     |
| 2020 |   AAAI    |  InteractE   |
| 2020 |   AAAI    |    ParamE    |
| 2020 |    ACL    | ReInceptionE |
| 2020 |   IJCAI   |     HypE     |
| 2020 |  COLING   |     ArcE     |
| 2021 |   KBS*    |     KMAE     |
| 2021 |   NCA*    |    DMACM     |
| 2021 |   NAACL   |     EDGE     |
| 2021 |   ESWC    |    ConEx     |
| 2022 |   KBS*    |    JointE    |
| 2022 |    AI*    |    CTKGC     |

### Graph Networks

| Year | Source |  Methods  |
| :--: | :----: | :-------: |
| 2018 |  ESWC  |   R-GCN   |
| 2019 |  AAAI  |   SACN    |
| 2019 |  ACL   |    A2N    |
| 2019 |  ACL   |   KBGAT   |
| 2019 | IJCAI  |   M-GNN   |
| 2019 | IJCAI  |   RDGCN   |
| 2019 | IJCAI  |  VR-GCN   |
| 2019 | ICASSP |   GRNN    |
| 2020 |  ICLR  |  CompGCN  |
| 2020 |  ICLR  |   DPMPN   |
| 2020 |  AAAI  |   RGHAT   |
| 2020 |  CIKM  |   GAEAT   |
| 2021 |  KBS*  | CoRelatE  |
| 2021 |  KBS*  |   RHGNN   |
| 2021 |  KBS*  |   TAGAT   |
| 2021 |  ESA*  |   KGEL    |
| 2021 |  IS*   |  DA-GCN   |
| 2021 |  NC*   |   TRAR    |
| 2021 |  NC*   |   SRGCN   |
| 2021 |  NCA*  |  SD-GAT   |
| 2021 |  AHN*  |   TRFR    |
| 2021 |  ACL   |   EIGAT   |
| 2021 |  CIKM  | DisenKGAT |
| 2021 |  WWW   |  KE-GCN   |
| 2021 |  WWW   |   M2GNN   |
| 2022 |  NC*   |  HSKGCN   |
| 2022 |  WSDM  |   NoGE    |



## Informations

### Text

| Year |  Source   |     Methods     |
| :--: | :-------: | :-------------: |
| 2014 |   EMNLP   |     pTransE     |
| 2015 |   EMNLP   |  Jointly(desp)  |
| 2016 |   AAAI    |      DKRL       |
| 2016 |   IJCAI   |      TEKE       |
| 2017 |   AAAI    |       SSP       |
| 2017 |   IJCAI   | Jointly(A-LSTM) |
| 2017 |    ACL    |       FRN       |
| 2018 |   AAAI    |     ConMask     |
| 2018 |   AAAI    |    JointNRE     |
| 2018 | NAACL-HLT |       ATE       |
| 2019 |   AAAI    |       OWE       |
| 2019 |   IJCAI   |       WWV       |
| 2019 |   EMNLP   |      CaRe       |
| 2019 |   EMNLP   |      TCVAE      |
| 2019 |   EMNLP   |       CPL       |
| 2020 |   ISWC    |      BCRL       |
| 2021 |   NAACL   |      EDGE       |
| 2021 |    WWW    |      StAR       |

### Path

| Year | Source  |   Methods    |
| :--: | :-----: | :----------: |
| 2015 |  EMNLP  |   PTransE    |
| 2015 |  EMNLP  |   RTransE    |
| 2015 |  EMNLP  | TransE-COMP  |
| 2016 | COLING  |     GAKE     |
| 2017 |  EMNLP  |   DeepPath   |
| 2017 |  CIKM   |     TCE      |
| 2018 |  ICLR   |   MINERVA    |
| 2018 |  EMNLP  |  MultiHopKG  |
| 2019 |  ICML   |     RSN      |
| 2019 |  EMNLP  |   OPTransE   |
| 2020 |  AAAI   |     RPJE     |
| 2020 | NeurIPS | Interstellar |

### Type

| Year |  Source   |   Methods   |
| :--: | :-------: | :---------: |
| 2016 |   IJCAI   |    TKRL     |
| 2017 |   CIKM    |     ETE     |
| 2017 | ECML/PKDD |   TransT    |
| 2018 |    ACL    | TypeComplex |
| 2019 |    KDD    |    JOIE     |
| 2020 |    ACL    |  ConnectE   |
| 2020 |   EMNLP   |  AutoETER   |
| 2021 |   AAAI    |    TaRP     |
| 2021 |    WWW    | RETA-Grader |

### Hierarchy

| Year | Source |  Methods   |
| :--: | :----: | :--------: |
| 2016 | IJCAI  |    TKRL    |
| 2016 | SIGIR  |    HiRi    |
| 2018 |  AAAI  |  TransE-T  |
| 2018 | EMNLP  | TransE-HRS |
| 2020 |  AAAI  |    HAKE    |
| 2020 | IJCAI  |  TransRHS  |

### Neighborhood

| Year | Source  | Methods |
| :--: | :-----: | :-----: |
| 2016 | NeurIPS | Gaifman |
| 2016 | COLING  |  GAKE   |
| 2017 |  CIKM   |   TCE   |
| 2018 |   UAI   |  KBLRN  |
| 2018 |  CIKM   |  SENN   |
| 2018 |  ESWC   |  R-GCN  |
| 2019 |  AAAI   |   LAN   |
| 2019 |  AAAI   |  LENA   |
| 2019 |  AAAI   |  SACN   |
| 2019 |  EMNLP  |  CaRe   |
| 2019 |   WWW   | TransN  |
| 2020 |  AAAI   |  FSRL   |

## Augmentations

### Rules

| Year | Source  |   Methods   |
| :--: | :-----: | :---------: |
| 2015 |  IJCAI  |  r-TransE   |
| 2016 |  IJCAI  |   ProPPR    |
| 2016 |  EMNLP  |    KALE     |
| 2017 | NeurIPS |  Neural-LP  |
| 2018 |  AAAI   |    RUGE     |
| 2018 |  AAAI   |    RLvLR    |
| 2018 |   ACL   | ComplEx-NNE |
| 2018 |   UAI   |    KBLRN    |
| 2018 |  ISWC   |    RuleN    |
| 2019 |  AAAI   |    UKGE     |
| 2019 | NeurIPS |    DRUM     |
| 2019 | NeurIPS |  pLogicNet  |
| 2019 |  IJCAI  |   AnyBURL   |
| 2019 |   WWW   |    IterE    |
| 2020 |  ICLR   | Neural-LP-N |
| 2020 |  AAAI   |    RPJE     |
| 2020 |  EMNLP  | ASR-ComplEx |
| 2020 |  EMNLP  | RuleGuider  |
| 2020 |  EMNLP  |    MCMH     |
| 2020 |  CIKM   |    SLRE     |
| 2020 |  ICDM   |  HybridER   |
| 2021 |  AAAI   |    RARL     |

### Regularize

| Year |  Source   |   Methods   |
| :--: | :-------: | :---------: |
| 2015 |    ACL    |     SSE     |
| 2017 | ECML/PKDD |  ComplExR   |
| 2018 |    ACL    | ComplEx-NNE |
| 2018 |   ICML    |  ComplEx-N  |
| 2018 |   AAAI    |  ComplEx-L  |
| 2019 |   AAAI    |   SimplE+   |
| 2019 |    UAI    |     EM      |
| 2020 |  NeurIPS  |    DURA     |
| 2020 |   EMNLP   |   DA+CSTR   |
| 2020 |   CIKM    |    SLRE     |



### Negative Sampling

| Year |  Source   |  Methods  |
| :--: | :-------: | :-------: |
| 2014 |   AAAI    |  TransH   |
| 2018 |   AAAI    |   IGAN    |
| 2018 | NAACL-HLT |   KBGAN   |
| 2019 |   ICLR    |  RotatE   |
| 2019 |   ICDE    | NSCaching |
| 2020 |   EMNLP   |   SANS    |



## Emergents

### N-ary

| Year | Source  | Methods  |
| :--: | :-----: | :------: |
| 2016 |  IJCAI  | m-TransH |
| 2018 |   WWW   |   RAE    |
| 2019 |   WWW   |   NaLP   |
| 2020 | NeurIPS |   BoxE   |
| 2020 |   ACL   | NeuInfer |
| 2020 |  IJCAI  |   HypE   |
| 2020 |  EMNLP  |  STARE   |
| 2020 |   WWW   |   GETD   |
| 2020 |   WWW   |  HINGE   |
| 2021 |   WWW   |   RAW    |

### Temporal

| Year |  Source   |   Methods   |
| :--: | :-------: | :---------: |
| 2014 |   EMNLP   |    CTPs     |
| 2016 |   EMNLP   |  t-TransE   |
| 2016 |  COLING   | TransE-TAE  |
| 2017 |   AAAI    |    MLNs     |
| 2017 |   ICML    | Know-Evolve |
| 2018 |   EMNLP   |    HyTE     |
| 2018 |   EMNLP   | TA-DistMult |
| 2018 |    WWW    |   TTransE   |
| 2019 |   ICLR    |    DyRep    |
| 2020 |   ICLR    |  TComplEx   |
| 2020 |   AAAI    |  DE-SimplE  |
| 2020 |   AAAI    |  EvolveGCN  |
| 2020 |   IJCAI   |   DArtNet   |
| 2020 |   EMNLP   |   DyERNIE   |
| 2020 |   EMNLP   |   RE-NET    |
| 2020 |   EMNLP   |    TeMP     |
| 2020 |   EMNLP   |  TIMEPLEX   |
| 2020 |  COLING   |    TeRo     |
| 2020 |   CIKM    |    ToKE     |
| 2020 |   ISWC    |    ATiSE    |
| 2020 |    WWW    |    TDGNN    |
| 2021 |   KBS*    |    TimE     |
| 2021 |   ASC*    |    TPath    |
| 2021 |   ICLR    |    xERTE    |
| 2021 |   AAAI    |   ChronoR   |
| 2021 |   AAAI    |   CyGNet    |
| 2021 |   AAAI    |    NLSM     |
| 2021 |    ACL    |   CluSTeR   |
| 2021 |    ACL    |  HERCULES   |
| 2021 |   IJCAI   |   HIPNet    |
| 2021 |   EMNLP   |    TANGO    |
| 2021 |   EMNLP   |   TEA-GNN   |
| 2021 |   EMNLP   |     TEE     |
| 2021 |   EMNLP   |    TITer    |
| 2021 | NAACL-HLT |     KRE     |
| 2021 | NAACL-HLT |    RTFE     |
| 2021 | NAACL-HLT |    TeLM     |
| 2021 |    KDD    |    T-GAP    |
| 2021 |   SIGIR   |   RE-GCN    |
| 2021 |   SIGIR   |     TIE     |
| 2021 |   WSDM    |    DBKGE    |
| 2021 |  DASFAA   |  ST-ConvKB  |
| 2021 |   ESWC    |    RETRA    |
| 2022 |   KBS*    |   TuckERT   |
| 2022 |   WSDM    |    EvoKG    |

### Uncertain

| Year | Source | Methods |
| :--: | :----: | :-----: |
| 2017 |  CIKM  |  URGE   |
| 2019 |  AAAI  |  UKGE   |
| 2021 | IJCAI  | FocusE  |
| 2021 | NAACL  | BEUrRE  |
| 2021 | DASFAA |  GMUC   |
| 2021 |  AAAI  | PASSLEA |

### Transfer

| Year | Source | Methods |
| :--: | :----: | :-----: |
| 2017 | IJCAI  |  MEAN   |
| 2020 | COLING | KD-MKB  |
| 2021 |  WWW   | ATransN |
| 2021 |  WWW   |  MulDE  |

### Segmented

| Year | Source |  Methods   |
| :--: | :----: | :--------: |
| 2020 |  ACL   |    SEEK    |
| 2020 |  ACL   |    OTE     |
| 2021 | NAACL  | ProcrustEs |

### Recommendation

| Year | Source | Methods |
| :--: | :----: | :-----: |
| 2018 |  ESWC  |  CoFM   |
| 2019 |  WWW   |  KTUP   |
| 2020 |  WWW   |  UPGAN  |

### Few Shot

| Year | Source  |  Methods  |
| :--: | :-----: | :-------: |
| 2017 |  IJCAI  |   MEAN    |
| 2018 |  EMNLP  | GMatching |
| 2019 |  EMNLP  |   MetaR   |
| 2019 |  EMNLP  |   TCVAE   |
| 2019 |  EMNLP  | Meta-KGR  |
| 2020 |  AAAI   |   FSRL    |
| 2020 |  AAAI   |   ZSGAN   |
| 2020 | NeurIPS |    GEN    |
| 2020 |  EMNLP  |   FAAN    |
| 2020 |  EMNLP  |   FIRE    |
| 2021 |  SIGIR  |   GANA    |
| 2021 |  SIGIR  |   MetaP   |
| 2021 | DASFAA  |   GMUC    |



### Low Resource

| Year | Source |   Methods    |
| :--: | :----: | :----------: |
| 2020 | EMNLP  | Pretrain-KGE |
| 2020 |  WWW   |     wRAN     |
| 2021 | DASFAA |     SEwA     |

### Complex Query

| Year | Source  | Methods |
| :--: | :-----: | :-----: |
| 2018 | NeurIPS |   GQE   |
| 2020 |  ICLR   |   Q2B   |
| 2020 | NeurIPS |  BETAE  |
| 2020 | NeurIPS |  EmQL   |
| 2020 |   UAI   | TRACTOR |
| 2021 |  AAAI   |  BiQE   |
| 2021 |   KDD   | NewLook |

### Reinforcement Learning

| Year | Source  |   Methods    |
| :--: | :-----: | :----------: |
| 2017 |  EMNLP  |   DeepPath   |
| 2018 |  ICLR   |   MINERVA    |
| 2018 | NeurIPS |    M-Walk    |
| 2018 |  EMNLP  |  MultiHopKG  |
| 2020 |  AAAI   |     R2D      |
| 2020 |  IJCAI  |     RLH      |
| 2020 |  EMNLP  |     CPL      |
| 2020 |  EMNLP  |    DacKGR    |
| 2020 |  EMNLP  |  RuleGuider  |
| 2021 |  AAAI   |   PASSLEAF   |
| 2021 |  AAAI   | GaussianPath |



### Inductive Link Prediction

| Year | Source  |  Methods  |
| :--: | :-----: | :-------: |
| 2017 | NeurIPS | Neural-LP |
| 2018 |  ISWC   |   RuleN   |
| 2019 | NeurIPS |   DRUM    |
| 2020 |  ICML   |   GraIL   |
| 2020 |  ISWC   |   IELP    |
| 2021 |  AAAI   |   AAAI    |

# Papers

## Survey

- Yoshua Bengio, Aaron C. Courville, Pascal Vincent. **"Representation Learning: A Review and New Perspectives". Transactions on Pattern Analysis and Machine Intelligence 2013. Impact 16.389.** [*paper*](https://ieeexplore.ieee.org/document/6472238)
- Maximilian Nickel, Kevin Murphy, Volker Tresp, Evgeniy Gabrilovich. **"A Review ofRelational Machine Learning for Knowledge Graphs". Proceedings of the IEEE2016\. Impact 10.960.** [*paper*](https://ieeexplore.ieee.org/document/7358050)
- Quan Wang, Zhendong Mao, Bin Wang, Li Guo. **"Knowledge Graph Embedding: A Survey of Approaches and Applications". IEEE Transactions on Knowledge and Data Engineering 2017. Impact 6.976.** [*paper*](https://ieeexplore.ieee.org/document/8047276)
- HongYun Cai, Vincent W. Zheng, Kevin Chen-Chuan Chang. **"A Comprehensive Survey of Graph Embedding: Problems, Techniques, and Applications". IEEE Transactions on Knowledge and Data Engineering 2018. Impact 6.976.** [*paper*](https://ieeexplore.ieee.org/document/8294302)
- Xiaojun Chen, Shengbin Jia, Yang Xiang. **"A review: Knowledge reasoning over knowledge graph". Expert Systems with Applications 2020. Impact 6.953.** [*paper*](https://www.sciencedirect.com/science/article/pii/S0957417419306669?via%3Dihub)
- Aidan Hogan, Eva Blomqvist, Michael Cochez, Claudia D’amato, Gerard De Melo, Claudio Gutierrez, Sabrina Kirrane, José Emilio Labra Gayo, Roberto Navigli, Sebastian Neumaier, Axel-Cyrille Ngonga Ngomo, Axel Polleres, Sabbir M. Rashid,Anisa Rula, Lukas Schmelzeisen, Juan Sequeda, Steffen Staab, Antoine Zimmermann. **"Knowledge Graphs". ACM Computing Surveys 2021. Impact 10.282.** [*paper*](https://dl.acm.org/doi/10.1145/3447772)
- Erik Cambria, Shaoxiong Ji, Shirui Pan, Philip S. Yu. **"Knowledge graph representation and reasoning". Neurocomputing 2021. Impact 5.719.** [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S092523122100953X?via%3Dihub)
- Xuejie Hao, Zheng Ji, Xiuhong Li, Lizeyan Yin, Lu Liu, Meiying Sun, Qiang Liu, Rongjin Yang. **"Construction and Application of a Knowledge Graph". Remote Sensing 2021\. Impact 4.848.** [*paper*](https://www.mdpi.com/2072-4292/13/13/2511)
- Claudio Gutierrez, Juan F. Sequeda. **"Knowledge Graphs". Communications of theACM 2021. Impact 4.654.** [*paper*](https://dl.acm.org/doi/10.1145/3418294) 
- Andrea Rossi, Donatella Firmani, Antonio Matinata, Paolo Merialdo, Denilson Barbosa.**"Knowledge Graph Embedding for Link Prediction: A Comparative Analysis". ACM Transactions on Knowledge Discovery from Data 2021. Impact 2.713.** [*paper*](https://dl.acm.org/doi/10.1145/3424672)
- Ilaria Tiddi, Stefan Schlobach. **"Knowledge graphs as tools for explainable machine learning: A survey". Artificial Intelligence 2022.** [*paper*](https://www.sciencedirect.com/science/article/pii/S0004370221001788?via%3Dihub)
- Luigi Bellomarini, Ruslan R. Fayzrakhmanov, Georg Gottlob, Andrey Kravchenko,Eleonora Laurenza, Yavor Nenov, Stéphane Reissfelder, Emanuel Sallinger, Evgeny Sherkhonov, Sahar Vahdati, Lianlong Wu. **"Data science with Vadalog: Knowledge Graphs with machine learning and reasoning in practice". Future Generation Computer Systems 2022.** [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0167739X21004179?via%3Dihub)
- Mehwish Alam, Anna Fensel, Jorge Martínez Gil, Bernhard Moser, Diego Reforgiato Recupero, Harald Sack. **"Special Issue on Machine Learning and Knowledge Graphs". Future Generation Computer Systems 2022. Impact 2.713.** [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0167739X21004660?via%3Dihub)
- Shaoxiong Ji, Shirui Pan, Erik Cambria, Pekka Marttinen, Philip S. Yu. **"A Survey on Knowledge Graphs: Representation, Acquisition, and Applications". IEEE Transactions on Neural Networks and Learning Systems 2022. Impact 10.450.** [*paper*](https://ieeexplore.ieee.org/document/9416312)

## 2011

### Conference

#### AAAI

- **(SE)** Antoine Bordes, Jason Weston, Ronan Collobert, Yoshua Bengio. **"Learning Structured Embeddings of Knowledge Bases". AAAI 2011.** [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI11/paper/view/3659) :fire:

#### ICML

- **(RESCAL)** Nickel Maximilian, Tresp Volker, Kriegel Hans-Peter. **"A Three-Way Model for Collective Learning on Multi-Relational Data". ICML 2011.** [*paper*](https://icml.cc/2011/papers/438_icmlpaper.pdf) [*code*](https://github.com/mnick/scikit-kge) :fire:

## 2012

### Conference

#### NeurIPS

- **(LFM)** Rodolphe Jenatton, Nicolas L. Roux, Antoine Bordes, Guillaume R. Obozinski.**"A Latent Factor Model for Highly Multi-relational Data". NeurIPS 2012.** [*paper*](http://papers.nips.cc/paper/4744-a-latent-factor-model-for-highly-multi-relational-data) :fire:

## 2013

### Conference

#### NeurIPS

- **(NTN)** Richard Socher, Danqi Chen, Christopher D. Manning, Andrew Y. Ng.**"Reasoning With Neural Tensor Networks for Knowledge Base Completion". NeurIPS 2013.** [*paper*](http://papers.nips.cc/paper/5028-reasoning-with-neural-tensor-networks-for-knowledge-base-completion) [*reviews*](http://media.nips.cc/nipsbooks/nipspapers/paper_files/nips26/reviews/504.html) :fire:
- **(TransE)** Antoine Bordes, Nicolas Usunier, Alberto Garcia-Duran, Jason Weston,Oksana Yakhnenko. **"Translating Embeddings for Modeling Multi-relational Data".NeurIPS 2013.** [*paper*](http://papers.nips.cc/paper/5071-translating-embeddings-for-modeling-multi-relational-data) [*reviews*](http://media.nips.cc/nipsbooks/nipspapers/paper_files/nips26/reviews/1282.html) :fire:

## 2014

### Conference

#### AAAI

- **(TransH)** Zhen Wang, Jianwen Zhang, Jianlin Feng, Zheng Chen. **"Knowledge Graph Embedding by Translating on Hyperplanes". AAAI 2014.** [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI14/paper/view/8531) :fire:

#### EMNLP

- **(CTPs)** Derry Tanti Wijaya, Ndapandula Nakashole, Tom M. Mitchell. **"CTPs: Contextual Temporal Profiles for Time Scoping Facts using State Change Detection". EMNLP 2014.** [*paper*](https://www.aclweb.org/anthology/D14-1207/)
- **(pTransE)** Zhen Wang, Jianwen Zhang, Jianlin Feng, Zheng Chen. **"Knowledge Graph and Text Jointly Embedding". EMNLP 2014.** [*paper*](https://www.aclweb.org/anthology/D14-1167/) :fire:

#### KDD

- **(ER-MLP)** Xin Dong, Evgeniy Gabrilovich, Geremy Heitz, Wilko Horn, Ni Lao, Kevin Murphy, Thomas Strohmann, Shaohua Sun, Wei Zhang. **"Knowledge vault: a webscale approach to probabilistic knowledge fusion". KDD 2014.** [*paper*](https://dl.acm.org/doi/10.1145/2623330.2623623) :fire:

## 2015

### Journal

#### Data Mining and Knowledge Discovery

- **(GCTF)** Beyza Ermis, Evrim Acar, Ali Taylan Cemgil. **"Link prediction in heterogeneous data via generalized coupled tensor factorization". Data Mining and Knowledge Discovery 2015.** [*paper*](https://link.springer.com/article/10.1007/s10618-013-0341-y)

- **(PIDE)** Yu Zhao, Sheng Gao, Patrick Gallinari, Jun Guo. **"Knowledge base completion by learning pairwise-interaction differentiated embeddings". Data Mining and Knowledge Discovery 2015.** [*paper*](https://link.springer.com/article/10.1007/s10618-015-0430-1)

### Conference

#### ICLR

- **(DistMult)** Bishan Yang, Wen-tau Yih, Xiaodong He, Jianfeng Gao, Li Deng. **"Embedding Entities and Relations for Learning and Inference in Knowledge Bases". ICLR 2015.** [*paper*](https://arxiv.org/abs/1412.6575) :fire:

#### AAAI

- **(TransR/CTransR)** Yankai Lin, Zhiyuan Liu, Maosong Sun, Yang Liu, Xuan Zhu.**"Learning Entity and Relation Embeddings for Knowledge Graph Completion". AAAI 2015.** [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI15/paper/view/9571) [*code*](https://github.com/thunlp/KB2E) :fire:

#### ACL

- **(SSE)** Shu Guo, Quan Wang, Bin Wang, Lihong Wang, Li Guo. **"Semantically Smooth Knowledge Graph Embedding". ACL 2015.** [*paper*](https://www.aclweb.org/anthology/P15-1009/) :fire:

- **(TransD)** Guoliang Ji, Shizhu He, Liheng Xu, Kang Liu, Jun Zhao. **"Knowledge Graph Embedding via Dynamic Mapping Matrix". ACL 2015.** [*paper*](https://www.aclweb.org/anthology/P15-1067/) :fire:

#### IJCAI

- **(r-TransE)** Quan Wang, Bin Wang, Li Guo. **"Knowledge Base Completion Using Embeddings and Rules". IJCAI 2015.** [*paper*](http://ijcai.org/Abstract/15/264) :fire:

#### EMNLP

- Yuanfei Luo, Quan Wang, Bin Wang, Li Guo. **"Context-Dependent Knowledge Graph Embedding". EMNLP 2015.** [*paper*](https://www.aclweb.org/anthology/D15-1191/)
- **(Jointly(desp))** Huaping Zhong, Jianwen Zhang, Zhen Wang, Hai Wan, Zheng Chen. **"Aligning Knowledge and Text Embeddings by Entity Descriptions". EMNLP 2015.** [*paper*](https://www.aclweb.org/anthology/D15-1031/) :fire:
- **(PTransE)** Yankai Lin, Zhiyuan Liu, Huanbo Luan, Maosong Sun, Siwei Rao, Song Liu.**"Modeling Relation Paths for Representation Learning of Knowledge Bases".EMNLP 2015.** [*paper*](https://www.aclweb.org/anthology/D15-1082/) [*code*](https://github.com/thunlp/KB2E) :fire:
- **(RTransE)** Alberto Garcia-Duran, Antoine Bordes, Nicolas Usunier. **"Composing Relationships with Translations". EMNLP 2015.** [*paper*](https://www.aclweb.org/anthology/D15-1034/)
- **(TransE-COMP)** Kelvin Guu, John Miller, Percy Liang. **"Traversing Knowledge Graphs in Vector Space". EMNLP 2015.** [*paper*](https://www.aclweb.org/anthology/D15-1038/) [*code*](https://github.com/millerjohnp/traversing_knowledge_graphs) :fire:

#### CIKM

- **(INS)** Zhuoyu Wei, Jun Zhao, Kang Liu, Zhenyu Qi, Zhengya Sun, Guanhua Tian. **"Large-scale Knowledge Base Completion: Inferring via Grounding Network Sampling over Selected Instances". CIKM 2015.** [*paper*](https://dl.acm.org/citation.cfm?doid=2806416.2806513)
- **(KG2E)** Shizhu He, Kang Liu, Guoliang Ji, Jun Zhao. **"Learning to Represent Knowledge Graphs with Gaussian Embedding". CIKM 2015.** [*paper*](https://dl.acm.org/citation.cfm?doid=2806416.2806502) :fire:

#### WWW

- **(AMDC)** Hiroshi Kajino, Akihiro Kishimoto, Adi Botea, Elizabeth M. Daly, Spyros Kotoulas. **"Active Learning for Multi-relational Data Construction". WWW 2015.**[*paper*](https://dl.acm.org/doi/10.1145/2736277.2741103)

## 2016

### Journal

#### Data Mining and Knowledge Discovery

- **(ARIMA)** Ismail Günes, Sule Gündüz Ögüdücü, Zehra Çataltepe. **"Link prediction using time series of neighborhood-based node similarity scores". Data Mining and Knowledge Discovery 2016.** [*paper*](https://link.springer.com/article/10.1007/s10618-015-0407-0)

### Conference

#### AAAI

- **(DKRL)** Ruobing Xie, Zhiyuan Liu, Jia Jia, Huanbo Luan, Maosong Sun. **"Representation Learning of Knowledge Graphs with Entity Descriptions". AAAI 2016.** [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/view/12216) [*code*](https://github.com/xrb92/DKRL) :fire: :boom:
- **(HolE)** Maximilian Nickel, Lorenzo Rosasco, Tomaso Poggio. **"Holographic Embeddings of Knowledge Graphs". AAAI 2016.** [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/view/12484) [*code*](https://github.com/mnick/holographic-embeddings) :fire: :boom:
- **(TransA)** Yantao Jia, Yuanzhuo Wang, Hailun Lin, Xiaolong Jin, Xueqi Cheng. **"Locally Adaptive Translation for Knowledge Graph Embedding". AAAI 2016.** [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/view/12018) :fire:
- **(TranSparse)** Guoliang Ji, Kang Liu, Shizhu He, Jun Zhao. **"Knowledge Graph Completion with Adaptive Sparse Transfer Matrix". AAAI 2016.** [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/view/11982) :fire:

#### NeurIPS

- **(Gaifman)** Mathias Niepert. **"Discriminative Gaifman Models". NeurIPS 2016.** [*paper*](http://papers.nips.cc/paper/6098-discriminative-gaifman-models) [*reviews*](http://media.nips.cc/nipsbooks/nipspapers/paper_files/nips29/reviews/1689.html)

#### ACL

- Teng Long, Ryan Lowe, Jackie Chi Kit Cheung, Doina Precup. **"Leveraging Lexical Resources for Learning Entity Embeddings in Multi-Relational Data". ACL 2016.** [*paper*](https://www.aclweb.org/anthology/P16-2019/)

- **(TransG)** Han Xiao, Minlie Huang, Xiaoyan Zhu. **"TransG: A Generative Model for Knowledge Graph Embedding". ACL 2016.** [*paper*](https://www.aclweb.org/anthology/P16-1219/) [*code*](https://github.com/BookmanHan/Embedding) :fire:

#### ICML

- **(ComplEx)** Théo Trouillon, Johannes Welbl, Sebastian Riedel, Éric Gaussier, Guillaume Bouchard. **"Complex Embeddings for Simple Link Prediction". ICML 2016.** [*paper*](http://proceedings.mlr.press/v48/trouillon16.html) [*code*](https://github.com/ttrouill/complex) :fire: :boom:

#### IJCAI

- **(KR-EAR)** Yankai Lin, Zhiyuan Liu, Maosong Sun. **"Knowledge Representation Learning with Entities, Attributes and Relations". IJCAI 2016.** [*paper*](http://www.ijcai.org/Abstract/16/407) [*code*](https://github.com/thunlp/KR-EAR)
- **(ManifoldE)** Han Xiao, Minlie Huang, Xiaoyan Zhu. **"From One Point to a Manifold: Knowledge Graph Embedding for Precise Link Prediction". IJCAI 2016.** [*paper*](http://www.ijcai.org/Abstract/16/190) [*code*](https://github.com/BookmanHan/Embedding):fire:
- **(m-TransH)** Jianfeng Wen, Jianxin Li, Yongyi Mao, Shini Chen, Richong Zhang. **"On the Representation and Embedding of Knowledge Bases beyond Binary Relations". IJCAI 2016.** [*paper*](https://www.ijcai.org/Abstract/16/188)
- **(ProPPR)** William Yang Wang, William W. Cohen. **"Learning First-Order Logic Embeddings via Matrix Factorization". IJCAI 2016.** [*paper*](http://www.ijcai.org/Abstract/16/304) [*code*](https://github.com/TeamCohen/ProPPR)
- **(TEKE)** Zhigang Wang, Juanzi Li. **"Text-Enhanced Representation Learning for Knowledge Graph". IJCAI 2016.** [*paper*](http://www.ijcai.org/Abstract/16/187) :fire:
- **(TKRL)** Ruobing Xie, Zhiyuan Liu, Maosong Sun. **"Representation Learning of Knowledge Graphs with Hierarchical Types". IJCAI 2016.** [*paper*](http://www.ijcai.org/Abstract/16/421) [*code*](https://github.com/thunlp/TKRL) :fire:

#### EMNLP

- **(KALE)** Shu Guo, Quan Wang, Lihong Wang, Bin Wang, Li Guo.**"Jointly Embedding Knowledge Graphs and Logical Rules". EMNLP 2016.** [*paper*](https://www.aclweb.org/anthology/D16-1019/) [*code*](https://github.com/iieir-km/KALE) :fire:
- **(t-TransE)** Tingsong Jiang, Tianyu Liu, Tao Ge, Lei Sha, Sujian Li, Baobao Chang, Zhifang Sui. **"Encoding Temporal Information for Time-Aware Link Prediction".EMNLP 2016.** [*paper*](https://www.aclweb.org/anthology/D16-1260/)

#### COLING

- **(GAKE)** Jun Feng, Minlie Huang, Yang Yang, Xiaoyan Zhu. **"GAKE: Graph Aware Knowledge Embedding". COLING 2016.** [*paper*](https://www.aclweb.org/anthology/C16-1062/) [*code*](https://github.com/JuneFeng/GAKE)
- **(TransE-TAE)** Tingsong Jiang, Tianyu Liu, Tao Ge, Lei Sha, Baobao Chang, Sujian Li, Zhifang Sui. **"Towards Time-Aware Knowledge Graph Completion". COLING 2016.** [*paper*](https://www.aclweb.org/anthology/C16-1161/)

#### KR

- **(FTransE)** Jun Feng, Minlie Huang, Mingdong Wang, Mantong Zhou, Yu Hao, XiaoyanZhu. **"Knowledge Graph Embedding by Flexible Translation". KR 2016.** [*paper*](https://www.aaai.org/ocs/index.php/KR/KR16/paper/view/12887) [*code*](http://ml.knu.ac.kr/lppKE)

#### NAACL

- **(lppTransE)** Hee-Geun Yoon, Hyun-Je Song, Seong-Bae Park, Se-Young Park. "A Translation-Based Knowledge Graph Embedding Preserving Logical Property of Relations". HLT-NAACL 2016. [*paper*](https://www.aclweb.org/anthology/N16-1105)
- **(STransE)** Dat Quoc Nguyen, Kairit Sirts, Lizhen Qu, Mark Johnson. **"STransE: A Novel Embedding Model of Entities and Relationships in Knowledge Bases". HLTNAACL 2016.** [*paper*](https://www.aclweb.org/anthology/N16-1054/) [*code*](https://github.com/datquocnguyen/STransE) :fire:

#### SIGIR

- **(HiRi)** Qiao Liu, Liuyi Jiang, Minghao Han, Yao Liu, Zhiguang Qin. **"Hierarchical Random Walk Inference in Knowledge Graphs". SIGIR 2016.** [*paper*](https://dl.acm.org/doi/10.1145/2911451.2911509)

#### ESWC

- **(mwNN)** Yinchong Yang, Cristóbal Esteban, Volker Tresp. **"Embedding Mapping Approaches for Tensor Factorization and Knowledge Graph Modelling". ESWC 2016.** [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-319-34129-3_13)

## 2017

### Journal

#### Information Sciences

- **(LPMR)** Caiyan Dai, Ling Chen, Bin Li, Yun Li. **"Link prediction in multi-relational networks based on relational similarity". Information Sciences 2017.** [*paper*](https://www.sciencedirect.com/science/article/pii/S0020025517304139?via%3Dihub) :fire:

#### IEEE Transactions on Knowledge and Data Engineering

- **(SSE)** Shu Guo, Quan Wang, Bin Wang, Lihong Wang, Li Guo. **"SSE: Semantically Smooth Embedding for Knowledge Graphs". IEEE Transactions on Knowledge and Data Engineering 2017.** [*paper*](https://ieeexplore.ieee.org/document/7779046) :fire:

- **(TRANSFER)** Xiaochi Wei, Heyan Huang, Liqiang Nie, Hanwang Zhang, Xianling Mao, Tat-Seng Chua. **"I Know What You Want to Express: Sentence Element Inference by Incorporating External Knowledge Base". IEEE Transactions on Knowledge and Data Engineering 2017.** [*paper*](https://ieeexplore.ieee.org/document/7723822) [*code*](https://datapublication.wixsite.com/transfer)

#### Knowledge-based Systems

- **(searchWeb)** Lidong Bing, Zhiming Zhang, Wai Lam, William W. Cohen. **"Towards a language-independent solution: Knowledge base completion by searching the Web and deriving language pattern". Knowledge-based Systems 2017.** [*paper*](https://www.sciencedirect.com/science/article/pii/S0950705116303859?via%3Dihub)

#### Neurocomputing

- **(TransPES)** Yu Wu, Tingting Mu, John Yannis Goulermas. **"Translating on pairwise entity space for knowledge graph embedding". Neurocomputing 2017.** [*paper*](https://www.sciencedirect.com/science/article/pii/S0925231217307968?via%3Dihub) [*code*](https://github.com/while519/TranPES)

#### Journal of Machine Learning Research

- **(ComplEx)** Théo Trouillon, Christopher R. Dance, Éric Gaussier, Johannes Welbl, Sebastian Riedel, Guillaume Bouchard. **"Knowledge Graph Completion via Complex Tensor Factorization". Journal of Machine Learning Research 2017.** [*paper*](http://jmlr.org/papers/v18/16-563.html) [*code*](https://github.com/ttrouill/complex)

### Conference

#### AAAI

- **(MLNs)** Melisachew Wudage Chekol, Giuseppe Pirr , Joerg Schoenfisch, Heiner Stuckenschmidt. **"Marrying Uncertainty and Time in Knowledge Graphs". AAAI 2017.** [*paper*](https://aaai.org/ocs/index.php/AAAI/AAAI17/paper/view/14730)
- **(ProjE)** Baoxu Shi, Tim Weninger. **"ProjE: Embedding Projection for Knowledge Graph Completion". AAAI 2017.** [*paper*](https://aaai.org/ocs/index.php/AAAI/AAAI17/paper/view/14279) [*code*](https://github.com/bxshi/ProjE) :fire:
- **(puTransE)** Yi Tay, Luu Anh Tuan, Siu Cheung Hui. **"Non-Parametric Estimation of Multiple Embeddings for Link Prediction on Dynamic Knowledge Graphs". AAAI 2017.** [*paper*](https://aaai.org/ocs/index.php/AAAI/AAAI17/paper/view/14524)
- **(SSP)** Han Xiao, Minlie Huang, Lian Meng, Xiaoyan Zhu. **"SSP: Semantic Space Projection for Knowledge Graph Embedding with Text Descriptions". AAAI 2017.**[*paper*](https://aaai.org/ocs/index.php/AAAI/AAAI17/paper/view/14306) [*code*](https://github.com/BookmanHan/Embedding) :fire:

#### NeurIPS

- **(Neural-LP)** Fan Yang, Zhilin Yang, William W. Cohen. **"Differentiable Learning of Logical Rules for Knowledge Base Reasoning". NeurIPS 2017.** [*paper*](http://papers.nips.cc/paper/6826-differentiable-learning-of-logical-rules-for-knowledge-base-reasoning) [*reviews*](http://media.nips.cc/nipsbooks/nipspapers/paper_files/nips30/reviews/1347.html) [*code*](https://github.com/fanyangxyz/Neural-LP):fire:
- **(NTPs)** Tim Rocktäschel, Sebastian Riedel. **"End-to-end Differentiable Proving". NeurIPS 2017.** [*paper*](https://proceedings.neurips.cc/paper/2017/hash/b2ab001909a8a6f04b51920306046ce5-Abstract.html)

#### ACL

- **(FRN)** Alexandros Komninos, Suresh Manandhar. **"Feature-Rich Networks for Knowledge Base Completion". ACL 2017.** [*paper*](https://www.aclweb.org/anthology/P17-2051/)
- **(ITransF)** Qizhe Xie, Xuezhe Ma, Zihang Dai, Eduard Hovy. **"An Interpretable Knowledge Transfer Model for Knowledge Base Completion". ACL 2017.** [*paper*](https://www.aclweb.org/anthology/P17-1088/)

#### ICML

- **(ANALOGY)** Hanxiao Liu, Yuexin Wu, Yiming Yang. **"Analogical Inference for Multirelational Embeddings". ICML 2017.** [*paper*](http://proceedings.mlr.press/v70/liu17d.html) [*code*](https://github.com/quark0/ANALOGY) :fire:
- **(Know-Evolve)** Rakshit Trivedi, Hanjun Dai, Yichen Wang, Le Song. **"Know-Evolve: Deep Temporal Reasoning for Dynamic Knowledge Graphs". ICML 2017.** [*paper*](http://proceedings.mlr.press/v70/trivedi17a.html):fire:
- **(MPNN)** Justin Gilmer, Samuel S. Schoenholz, Patrick F. Riley, Oriol Vinyals, George E.Dahl. **"Neural Message Passing for Quantum Chemistry". ICML 2017.** [*paper*](http://proceedings.mlr.press/v70/gilmer17a.html)

#### IJCAI

- (IKRL) Ruobing Xie, Zhiyuan Liu, Huanbo Luan, Maosong Sun. "Image-embodied Knowledge Representation Learning". IJCAI 2017. [*paper*](https://www.ijcai.org/proceedings/2017/438) [*code*](https://github.com/thunlp/IKRL)
- (Jointly(A-LSTM)) Jiacheng Xu, Xipeng Qiu, Kan Chen, Xuanjing Huang. "Knowledge Graph Representation with Jointly Structural and Textual Encoding". IJCAI 2017. [*paper*](https://www.ijcai.org/proceedings/2017/183) [*code*](https://github.com/jiacheng-xu/Attn-KGE) :fire:
- MEAN Takuo Hamaguchi, Hidekazu Oiwa, Masashi Shimbo, Yuji Matsumoto."Knowledge Transfer for Out-of-Knowledge-Base Entities : A Graph Neural Network Approach". IJCAI 2017. [*paper*](https://www.ijcai.org/proceedings/2017/250)
- IPTransE Hao Zhu, Ruobing Xie, Zhiyuan Liu, Maosong Sun. "Iterative Entity Alignment via Joint Knowledge Embeddings". IJCAI 2017. [*paper*](https://www.ijcai.org/proceedings/2017/595)

#### UAI

- (ASR-ComplEx) Pasquale Minervini, Thomas Demeester, Tim Rocktäschel, Sebastian Riedel. "Adversarial Sets for Regularising Neural Link Predictors". UAI 2017. [*paper*](http://auai.org/uai2017/proceedings/papers/306.pdf)

#### EMNLP

- (DeepPath) Wenhan Xiong, Thien Hoang, William Yang Wang. "DeepPath: A Reinforcement Learning Method for Knowledge Graph Reasoning". EMNLP 2017. CCF B. Cite 180. [*paper*](https://www.aclweb.org/anthology/D17-1060/) :fire:
- (Sparsity) Jay Pujara, Eriq Augustine, Lise Getoor. "Sparsity and Noise: Where Knowledge Graph Embeddings Fall Short". EMNLP 2017. [*paper*](https://www.aclweb.org/anthology/D17-1184/) [*code*](https://github.com/linqs/pujara-emnlp17)

#### CIKM

- (CombinE) Zhen Tan, Xiang Zhao, Wei Wang. "Representation Learning of Large-Scale Knowledge Graphs via Entity Feature Combinations". CIKM 2017. [*paper*](https://dl.acm.org/doi/10.1145/3132847.3132961)
- (Correlation) Soumajit Pal, Jacopo Urbani. "Enhancing Knowledge Graph Completion By Embedding Correlations". CIKM 2017. [*paper*](https://dl.acm.org/doi/10.1145/3132847.3133143) [*code*](https://github.com/karmaresearch/statlearning)
- (ETE) Changsung Moon, Paul Jones, Nagiza F. Samatova. "Learning Entity Type Embeddings for Knowledge Graph Completion". CIKM 2017. [*paper*](https://dl.acm.org/doi/10.1145/3132847.3133095)
- (TCE) Jun Shi, Huan Gao, Guilin Qi, Zhangquan Zhou. "Knowledge Graph Embedding with Triple Context". CIKM 2017. [*paper*](https://dl.acm.org/doi/10.1145/3132847.3133119) [*code*](https://github.com/juneshi0315/TCE)
- (TransE-RS) Xiaofei Zhou, Qiannan Zhu, Ping Liu, Li Guo. "Learning Knowledge Embeddings by Combining Limit-based Scoring Loss". CIKM 2017. [*paper*](https://dl.acm.org/doi/10.1145/3132847.3132939)
- (URGE) Jiafeng Hu, Reynold Cheng, Zhipeng Huang, Yixiang Fang, Siqiang Luo. "On Embedding Uncertain Graphs". CIKM 2017. [*paper*](https://dl.acm.org/doi/10.1145/3132847.3132885)

#### WSDM

- (RSTE) Yi Tay, Anh Tuan Luu, Siu Cheung Hui, Falk Brauer. "Random Semantic Tensor Ensemble for Scalable Knowledge Graph Link Prediction". WSDM 2017. [*paper*](https://dl.acm.org/doi/10.1145/3018661.3018695)

#### ECML-PKDD

- (TransT) Shiheng Ma, Jianhui Ding, Weijia Jia, Kun Wang, Minyi Guo. "TransT: TypeBased Multiple Embedding Representations for Knowledge Graph Completion". ECML/PKDD 2017. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-319-71249-9_43)

#### WWW

- (ORC) Wen Zhang. "Knowledge Graph Embedding with Diversity of Structures". WWW 2017. [*paper*](https://dl.acm.org/doi/10.1145/3041021.3053380)
- (TransR-PNS) Vibhor Kanojia, Hideyuki Maeda, Riku Togashi, Sumio Fujita. "Enhancing Knowledge Graph Embedding with Probabilistic Negative Sampling". WWW 2017. [*paper*](https://dl.acm.org/doi/10.1145/3041021.3054238)

## 2018

### Journal

#### Knowledge-based Systems

- (PaSKoGE) Yantao Jia, Yuanzhuo Wang, Xiaolong Jin, Xueqi Cheng. "Path-specific knowledge graph embedding". Knowledge-based Systems 2018. [*paper*](https://www.sciencedirect.com/science/article/pii/S0950705118301448?via%3Dihub)

#### Cognitive Computation

- (VBNTD) Lirong He, Bin Liu, Guangxi Li, Yongpan Sheng, Yafang Wang, Zenglin Xu. "Knowledge Base Completion by Variational Bayesian Neural Tensor Decomposition". Cognitive Computation 2018. [*paper*](https://link.springer.com/article/10.1007%2Fs12559-018-9565-x) :fire:

### Conference

#### ICLR

- (MINERVA) Rajarshi Das, Shehzaad Dhuliawala, Manzil Zaheer, Luke Vilnis, Ishan Durugkar, Akshay Krishnamurthy, Alex Smola, Andrew McCallum. "Go for a Walk and Arrive at the Answer: Reasoning Over Paths in Knowledge Bases using Reinforcement Learning". ICLR 2018. [*paper*](https://openreview.net/forum?id=Syg-YfWCW) [*code*](https://github.com/shehzaadzd/MINERVA) :fire:

#### AAAI

- (CKRL) Ruobing Xie, Zhiyuan Liu, Fen Lin, Leyu Lin. "Does William Shakespeare REALLY Write Hamlet? Knowledge Representation Learning With Confidence". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16577) [*code*](https://github.com/thunlp/CKRL)
- (ComplEx-L1) Hitoshi Manabe, Katsuhiko Hayashi, Masashi Shimbo. "Data-Dependent Learning of Symmetric/Antisymmetric Relations for Knowledge Base Completion". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16211) [*code*](https://github.com/mana-ysh/symmetry-learning-kgc)
- (ConMask) Baoxu Shi, Tim Weninger. "Open-World Knowledge Graph Completion". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16055) [*code*](https://github.com/bxshi/ConMask) :fire:
- (ConvE) Tim Dettmers, Pasquale Minervini, Pontus Stenetorp, Sebastian Riedel."Convolutional 2D Knowledge Graph Embeddings". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/17366) [*code*](https://github.com/TimDettmers/ConvE) :fire:
- (IGAN) Peifeng Wang, Shuangyin Li, Rong Pan. "Incorporating GAN for Negative Sampling in Knowledge Representation Learning". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16094)
- (JointNRE) Xu Han, Zhiyuan Liu, Maosong Sun. "Neural Knowledge Acquisition via Mutual Attention Between Knowledge Graph and Text". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16691) [*code*](https://github.com/thunlp/JointNRE):fire:
- Yanjie Wang, Rainer Gemulla, Hui Li. "On Multi-Relational Link Prediction with Bilinear Models". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16900) [*code*](https://github.com/y-j-wang/b4l)
- (RUGE) Shu Guo, Quan Wang, Lihong Wang, Bin Wang, Li Guo. "Knowledge Graph Embedding With Iterative Guidance From Soft Rules". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16369) [*code*](https://github.com/iieir-km/RUGE) :fire:
- (TorusE) Takuma Ebisu, Ryutaro Ichise. "TorusE: Knowledge Graph Embedding on a Lie Group". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16227) [*code*](https://github.com/TakumaE/TorusE) :fire:
- (TransE-T) Richong Zhang, Fanshuang Kong, Chenyue Wang, Yongyi Mao. "Embedding of Hierarchically Typed Knowledge Bases". AAAI 2018. [*paper*](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16539) [*code*](https://github.com/fskong/Embedding_of_Hierarchically_Typed_KB)

#### NeurIPS

- (GQE) William L. Hamilton, Payal Bajaj, Marinka Zitnik, Dan Jurafsky, Jure Leskovec. "Embedding Logical Queries on Knowledge Graphs". NeurIPS 2018. [*paper*](http://papers.nips.cc/paper/7473-embedding-logical-queries-on-knowledge-graphs) [*reviews*](http://media.nips.cc/nipsbooks/nipspapers/paper_files/nips31/reviews/1018.html) [*code*](https://github.com/williamleif/graphqembed) :fire:
- (HolEX) Yexiang Xue, Yang Yuan, Zhitian Xu, Ashish Sabharwal. "Expanding Holographic Embeddings for Knowledge Completion". NeurIPS 2018. [*paper*](https://proceedings.neurips.cc/paper/2018/hash/dd28e50635038e9cf3a648c2dd17ad0a-Abstract.html)
- (SimplE) Seyed Mehran Kazemi, David Poole. "SimplE Embedding for Link Prediction in Knowledge Graphs". NeurIPS 2018. [*paper*](http://papers.nips.cc/paper/7682-simple-embedding-for-link-prediction-in-knowledge-graphs) [*reviews*](http://media.nips.cc/nipsbooks/nipspapers/paper_files/nips31/reviews/2093.html) [*code*](https://github.com/Mehran-k/SimplE) :fire:
- (M-Walk) Yelong Shen, Jianshu Chen, Po-Sen Huang, Yuqing Guo, Jianfeng Gao. "M-Walk: Learning to Walk over Graphs using Monte Carlo Tree Search". NeurIPS 2018. [*paper*](https://proceedings.neurips.cc/paper/2018/hash/c6f798b844366ccd65d99bc7f31e0e02-Abstract.html)

#### ACL

- (ComplEx-NNE) Boyang Ding, Quan Wang, Bin Wang, Li Guo. "Improving Knowledge Graph Embedding Using Simple Constraints". ACL 2018. CCF A. Cite 48\. [*paper*](https://www.aclweb.org/anthology/P18-1011/) [*code*](https://github.com/iieir-km/ComplEx-NNE_AER) :fire:
- (Joint+COMP) Ryo Takahashi, Ran Tian, Kentaro Inui. "Interpretable and Compositional Relation Learning by Joint Training with an Autoencoder". ACL 2018. [*paper*](https://www.aclweb.org/anthology/P18-1200/) [*code*](https://github.com/tianran/glimvec)
- (KG-Geometry) Chandrahas, Aditya Sharma, Partha Talukdar. "Towards Understanding the Geometry of Knowledge Graph Embeddings". ACL 2018. [*paper*](https://www.aclweb.org/anthology/P18-1012/) [*code*](https://github.com/malllabiisc/kg-geometry) 
- (POE) Luke Vilnis, Xiang Li, Shikhar Murty, Andrew McCallum. "Probabilistic Embedding of Knowledge Graphs with Box Lattice Measures". ACL 2018. [*paper*](https://www.aclweb.org/anthology/P18-1025/)
- (TypeComplex) Prachi Jain, Pankaj Kumar, Mausam, Soumen Chakrabarti. "Type-Sensitive Knowledge Base Inference Without Explicit Type Supervision". ACL 2018. [*paper*](https://aclanthology.org/P18-2013/)

#### ICML

- (ComplEx-N3) Timothée Lacroix, Nicolas Usunier, Guillaume Obozinski. "Canonical Tensor Decomposition for Knowledge Base Completion". ICML 2018. [*paper*](http://proceedings.mlr.press/v80/lacroix18a.html) [*code*](https://github.com/facebookresearch/kbc):fire:

#### IJCAI

- (TransAt) Wei Qian, Cong Fu, Yu Zhu, Deng Cai, Xiaofei He. "Translating Embeddings for Knowledge Graph Completion with Relation Attention Mechanism". IJCAI 2018. [*paper*](https://www.ijcai.org/proceedings/2018/596) [*code*](https://github.com/ZJULearning/TransAt)
- (RLvLR) Pouya Ghiasnezhad Omran, Kewen Wang, Zhe Wang. "Scalable Rule Learning via Learning Representation". IJCAI 2018. [*paper*](https://www.ijcai.org/proceedings/2018/297)

#### EMNLP

- (GMatching) Wenhan Xiong, Mo Yu, Shiyu Chang, Xiaoxiao Guo, William Yang Wang. "One-Shot Relational Learning for Knowledge Graphs". EMNLP 2018. [*paper*](https://www.aclweb.org/anthology/D18-1223/) [*code*](https://github.com/xwhan/One-shot-Relational-Learning)
- (HyTE) Shib Sankar Dasgupta, Swayambhu Nath Ray, Partha Talukdar. "HyTE: Hyperplane-based Temporally aware Knowledge Graph Embedding". EMNLP 2018\. [*paper*](https://www.aclweb.org/anthology/D18-1225/) [*code*](https://github.com/malllabiisc/HyTE) :fire:
- (MKBE) Pouya Pezeshkpour, Liyan Chen, Sameer Singh. "Embedding Multimodal Relational Data for Knowledge Base Completion". EMNLP 2018. [*paper*](https://www.aclweb.org/anthology/D18-1359/) [*code*](https://github.com/pouyapez/mkbe) 
- (MultiHopKG) Xi Victoria Lin, Richard Socher, Caiming Xiong. "Multi-Hop Knowledge Graph Reasoning with Reward Shaping". EMNLP 2018. [*paper*](https://www.aclweb.org/anthology/D18-1362/) [*code*](https://github.com/salesforce/MultiHopKG) :fire:
- (TA-DistMult) Alberto Garcia-Duran, Sebastijan Dumančić, Mathias Niepert. "Learning Sequence Encoders for Temporal Knowledge Graph Completion". EMNLP 2018. [*paper*](https://www.aclweb.org/anthology/D18-1516/) [*dataset*](https://github.com/nle-ml/mmkb)
- (TransC) Xin Lv, Lei Hou, Juanzi Li, Zhiyuan Liu. "Differentiating Concepts and Instances for Knowledge Graph Embedding". EMNLP 2018. [*paper*](https://www.aclweb.org/anthology/D18-1222/) [*code*](https://github.com/davidlvxin/TransC)
- (TransE-HRS) Zhao Zhang, Fuzhen Zhuang, Meng Qu, Fen Lin, Qing He. "Knowledge Graph Embedding with Hierarchical Relation Structure". EMNLP 2018. [*paper*](https://www.aclweb.org/anthology/D18-1358/)

#### KR

- (OntologyE) Víctor Gutiérrez-Basulto, Steven Schockaert. "From Knowledge Graph Embedding to Ontology Embedding? An Analysis of the Compatibility between Vector Space Representations and Rules". KR 2018. [*paper*](https://aaai.org/ocs/index.php/KR/KR18/paper/view/18013)

#### UAI

- (KBLRN) Alberto García-Durán, Mathias Niepert. "KBlrn: End-to-End Learning of Knowledge Base Representations with Latent, Relational, and Numerical Features". UAI 2018. [*paper*](http://auai.org/uai2018/proceedings/papers/149.pdf) :fire:

#### CoNLL

- (CKBC) Itsumi Saito, Kyosuke Nishida, Hisako Asano, Junji Tomita. "Commonsense Knowledge Base Completion and Generation". CoNLL 2018. [*paper*](https://www.aclweb.org/anthology/K18-1014/)

#### NAACL

- (ATE) Bo An, Bo Chen, Xianpei Han, Le Sun. "Accurate Text-Enhanced Knowledge Graph Representation Learning". NAACL-HLT 2018. [*paper*](https://www.aclweb.org/anthology/N18-1068/)
- (ConvKB) Dai Quoc Nguyen, Tu Dinh Nguyen, Dat Quoc Nguyen, Dinh Phung. "A Novel Embedding Model for Knowledge Base Completion Based on Convolutional Neural Network". NAACL-HLT 2018. [*paper*](https://www.aclweb.org/anthology/N18-2053/) [*code*](https://github.com/daiquocnguyen/ConvKB) :fire:
- (KBGAN) Liwei Cai, William Yang Wang. "KBGAN: Adversarial Learning for Knowledge Graph Embeddings". NAACL-HLT 2018. [*paper*](https://www.aclweb.org/anthology/N18-1133/) [*code*](https://github.com/cai-lw/KBGAN) :fire:

#### SIGIR

- (Max-K Criterion) Jiajie Mei, Richong Zhang, Yongyi Mao, Ting Deng. "On Link Prediction in Knowledge Bases: Max-K Criterion and Prediction Protocols". SIGIR 2018. [*paper*](https://dl.acm.org/doi/10.1145/3209978.3210029)
- (TransN) Chun-Chih Wang, Pu-Jen Cheng. "Translating Representations of Knowledge Graphs with Neighbors". SIGIR 2018. [*paper*](https://dl.acm.org/doi/10.1145/3209978.3210085)

#### CIKM

- (CACL) Byungkook Oh, Seungmin Seo, Kyong-Ho. "Knowledge Graph Completion by Context-Aware Convolutional Learning with Multi-Hop Neighborhoods". CIKM 2018. [*paper*](https://dl.acm.org/doi/10.1145/3269206.3271769)
- (MultiE) Zhao Zhang, Fuzhen Zhuang, Zheng-Yu Niu, Deqing Wang, Qing He. "MultiE: Multi-Task Embedding for Knowledge Base Completion". CIKM 2018. [*paper*](https://dl.acm.org/doi/10.1145/3269206.3269295)
- (Re-evaluat) Farahnaz Akrami, Lingbing Guo, Wei Hu, Chengkai Li. "Re-evaluating Embedding-Based Knowledge Graph Completion Methods". CIKM 2018. [*paper*](https://dl.acm.org/doi/10.1145/3269206.3269266)
- (SENN) Saiping Guan, Xiaolong Jin, Yuanzhuo Wang, Xueqi Cheng. "Shared Embedding Based Neural Networks for Knowledge Graph Completion". CIKM 2018. [*paper*](https://dl.acm.org/doi/10.1145/3269206.3271704)

#### ISWC

- (RuleN) Christian Meilicke, Manuel Fink, Yanjie Wang, Daniel Ruffinelli, Rainer Gemulla, Heiner Stuckenschmidt. "Fine-Grained Evaluation of Rule- and Embedding-Based Systems for Knowledge Graph Completion". ISWC 2018. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-00671-6_1)

#### ESWC

- (R-GCN) Michael Schlichtkrull, Thomas N. Kipf, Peter Bloem, Rianne van den Berg, Ivan Titov, Max Welling. "Modeling Relational Data with Graph Convolutional Networks". ESWC 2018. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-319-93417-4_38) [*code*](https://github.com/tkipf/relational-gcn) :fire:
- (CoFM) Guangyuan Piao, John G. Breslin. "Transfer Learning for Item Recommendations and Knowledge Graph Completion in Item Related Domains via a Co-Factorization Model". ESWC 2018. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-319-93417-4_32)

#### WWW

- (RAE) Richong Zhang, Junpeng Li, Jiajie Mei, Yongyi Mao. "Scalable Instance Reconstruction in Knowledge Bases via Relatedness Affiliated Embedding". WWW 2018. [*paper*](https://dl.acm.org/doi/10.1145/3178876.3186017)
- (RuleQuality) Kaja Zupanc, Jesse Davis. "Estimating Rule Quality for Knowledge Base Completion with the Relationship between Coverage Assumption". WWW 2018. [*paper*](https://dl.acm.org/doi/10.1145/3178876.3186006)
- (TTransE) Julien Leblay, Melisachew Wudage Chekol. "Deriving Validity Time in Knowledge Graph". WWW 2018. [*paper*](https://dl.acm.org/doi/10.1145/3184558.3191639)

## 2019

### Journal

#### Applied Soft Computing

- (ProjFE) Huajing Liu, Luyi Bai, Xiangnan Ma, Wenting Yu, Changming Xu. "ProjFE: Prediction of fuzzy entity and relation for knowledge graph completion". Applied Soft Computing 2019. [*paper*](https://www.sciencedirect.com/science/article/pii/S1568494619302959?via%3Dihub)

#### Knowledge-based Systems

- (KEC) Niannian Guan, Dandan Song, Lejian Liao. "Knowledge graph embedding with concepts". Knowledge-based Systems 2019. [*paper*](https://www.sciencedirect.com/science/article/pii/S0950705118304945?via%3Dihub) :fire: :boom:

#### Future Generation Computer Systems

- (TKGE) Binling Nie, Shouqian Sun. "Knowledge graph embedding via reasoning over entities, relations, and text". Future Generation Computer Systems 2019. [*paper*](https://www.sciencedirect.com/science/article/pii/S0167739X17321593?via%3Dihub) :fire:

#### Information Processing and Management

- (MKRL) Xing Tang, Ling Chen, Jun Cui, Baogang Wei. "Knowledge representation learning with entity descriptions, hierarchical types, and textual relations". Information Processing and Management 2019. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0306457318303698?via%3Dihub)

#### Journal of Machine Learning Research

- Chengchun Shi, Wenbin Lu, Rui Song. "Determining the Number of Latent Factors in Statistical Multi-Relational Learning". Journal of Machine Learning Research 2019. [*paper*](http://jmlr.org/papers/v20/18-037.html)

#### Neural Computing and Applications

- (RPE) Xixun Lin, Yanchun Liang, Fausto Giunchiglia, Xiaoyue Feng, Renchu Guan. "Relation path embedding in knowledge graphs". Neural Computing and Applications 2019. [*paper*](https://link.springer.com/article/10.1007%2Fs00521-018-3384-6)

### Conference

#### ICLR

- (DyRep) Rakshit Trivedi, Mehrdad Farajtabar, Prasenjeet Biswal, Hongyuan Zha. "DyRep: Learning Representations over Dynamic Graphs". ICLR 2019. [*paper*](https://openreview.net/forum?id=HyePrhR5KX) :fire: :boom:
- (RotatE) Zhiqing Sun, Zhi-Hong Deng, Jian-Yun Nie, Jian Tang. "RotatE: Knowledge Graph Embedding by Relational Rotation in Complex Space". ICLR 2019. [*paper*](https://openreview.net/forum?id=HkgEQnRqYQ) [*code*](https://github.com/DeepGraphLearning/KnowledgeGraphEmbedding) :fire: :boom:

#### AAAI

- (LAN) PeiFeng Wang, Jialong Han, Chenliang Li, Rong Pan. "Logic Attention Based Neighborhood Aggregation for Inductive Knowledge Graph Embedding". AAAI 2019. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/4698) [*code*](https://github.com/wangpf3/LAN)
- (LENA) Fanshuang Kong, Richong Zhang, Yongyi Mao, Ting Deng. "LENA: LocalityExpanded Neural Embedding for Knowledge Base Completion". AAAI 2019. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/4144) [*code*](https://github.com/fskong/LENA)
- (OWE) Haseeb Shah, Johannes Villmow, Adrian Ulges, Ulrich Schwanecke, Faisal Shafait. "An Open-World Extension to Knowledge Graph Completion Models".AAAI 2019. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/4162) [*code*](https://github.com/haseebs/OWE)
- (SACN) Chao Shang, Yun Tang, Jing Huang, Jinbo Bi, Xiaodong He, Bowen Zhou. "End-to-End Structure-Aware Convolutional Networks for Knowledge Base Completion". AAAI 2019. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/4164) [*code*](https://github.com/JD-AI-Research-Silicon-Valley/SACN) :fire:
- (SimplE+) Bahare Fatemi, Siamak Ravanbakhsh, David Poole. "Improved Knowledge Graph Embedding Using Background Taxonomic Information". AAAI 2019. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/4231)
- (TransGate) Jun Yuan, Neng Gao, Ji Xiang. "TransGate: Knowledge Graph Embedding with Shared Gate Structure". AAAI 2019. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/4169)
- (UKGE) Xuelu Chen, Muhao Chen, Weijia Shi, Yizhou Sun, Carlo Zaniolo. "Embedding Uncertain Knowledge Graphs". AAAI 2019. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/4210) [*code*](https://github.com/stasl0217/UKGE)

#### NeurIPS

- (DRUM) Ali Sadeghian, Mohammadreza Armandpour, Patrick Ding, Daisy Zhe Wang. "DRUM: End-To-End Differentiable Rule Mining On Knowledge Graphs". NeurIPS 2019\. [*paper*](http://papers.nips.cc/paper/9669-drum-end-to-end-differentiable-rule-mining-on-knowledge-graphs) [*code*](https://github.com/alisadeghian/DRUM)
- (MuRP) Ivana Balaževic, Carl Allen, Timothy Hospedales. "Multi-relational Poincaré Graph Embeddings". NeurIPS 2019. [*paper*](http://papers.nips.cc/paper/8696-multi-relational-poincare-graph-embeddings) [*code*](https://github.com/ibalazevic/multirelational-poincare) :fire:
- (pLogicNet) Meng Qu, Jian Tang. "Probabilistic Logic Neural Networks for Reasoning". NeurIPS 2019. [*paper*](https://proceedings.neurips.cc/paper/2019/hash/13e5ebb0fa112fe1b31a1067962d74a7-Abstract.html)
- (QuatE) Shuai Zhangy, Yi Tay, Lina Yao, Qi Liu. "Quaternion Knowledge Graph Embeddings". NeurIPS 2019. [*paper*](http://papers.nips.cc/paper/8541-quaternion-knowledge-graph-embeddings) [*code*](https://github.com/cheungdaven/QuatE) :fire:

#### ACL

- (A2N) Trapit Bansal, Da-Cheng Juan, Sujith Ravi, Andrew McCallum. "A2N: Attending to Neighbors for Knowledge Graph Inference". ACL 2019. [*paper*](https://aclanthology.org/P19-1431/)
- (DihEdral) Canran Xu, Ruijiang Li. "Relation Embedding with Dihedral Group in Knowledge Graph". ACL 2019. [*paper*](https://www.aclweb.org/anthology/P19-1026/)
- (KBGAT) Deepak Nathani, Jatin Chauhan, Charu Sharma, Manohar Kaul. "Learning Attention-based Embeddings for Relation Prediction in Knowledge Graphs". ACL 2019. [*paper*](https://www.aclweb.org/anthology/P19-1466/) [*code*](https://github.com/deepakn97/relationPrediction) :fire: :boom:

#### ICML

- (RSN) Lingbing Guo, Zequn Sun, Wei Hu. "Learning to Exploit Long-term Relational Dependencies in Knowledge Graphs". ICML 2019. [*paper*](http://proceedings.mlr.press/v97/guo19c.html) [*code*](https://github.com/nju-websoft/RSN) :fire:

#### IJCAI

- (AnyBURL) Christian Meilicke, Melisachew Wudage Chekol, Daniel Ruffinelli, Heiner Stuckenschmidt. "Anytime Bottom-Up Rule Learning for Knowledge Graph Completion". IJCAI 2019. [*paper*](https://www.ijcai.org/proceedings/2019/435) [*code*](http://web.informatik.uni-mannheim.de/AnyBURL/)
- (Attack) Hengtong Zhang, Tianhang Zheng, Jing Gao, Chenglin Miao, Lu Su, Yaliang Li, Kui Ren. "Data Poisoning Attack against Knowledge Graph Embedding". IJCAI 2019. CCF A. Cite 6. [*paper*](https://www.ijcai.org/proceedings/2019/674)
- (M-GNN) Zihan Wang, Zhaochun Ren, Chunyu He, Peng Zhang, Yue Hu. "Robust Embedding with Multi-Level Structures for Link Prediction". IJCAI 2019. [*paper*](https://www.ijcai.org/proceedings/2019/728)
- (RDGCN) Yuting Wu, Xiao Liu, Yansong Feng, Zheng Wang, Rui Yan, Dongyan Zhao. "Relation-Aware Entity Alignment for Heterogeneous Knowledge Graphs". IJCAI 2019. [*paper*](https://www.ijcai.org/proceedings/2019/733)
- (TransMS) Shihui Yang, Jidong Tian, Honglun Zhang, Junchi Yan, Hao He, Yaohui Jin."TransMS: Knowledge Graph Embedding for Complex Relations by Multidirectional Semantics". IJCAI 2019. [*paper*](https://www.ijcai.org/proceedings/2019/268) 
- (VR-GCN) Rui Ye, Xin Li, Yujie Fang, Hongyu Zang, Mingzhong Wang. "A Vectorized Relational Graph Convolutional Network for Multi-Relational Network Alignment". IJCAI 2019. [*paper*](https://www.ijcai.org/Proceedings/2019/574)
- (WWV) Neil Veira, Brian Keng, Kanchana Padmanabhan, Andreas G. Veneris. "Unsupervised Embedding Enhancements of Knowledge Graphs using Textual Associations". IJCAI 2019. [*paper*](https://www.ijcai.org/proceedings/2019/725) [*code*](https://github.com/rubikloud/kg-text-embeddings)

#### EMNLP

- (AttnPath) Heng Wang, Shuangyin Li, Rong Pan, Mingzhi Mao. "Incorporating Graph Attention Mechanism into Knowledge Graph Reasoning Based on Deep Reinforcement Learning". EMNLP/IJCNLP 2019. [*paper*](https://www.aclweb.org/anthology/D19-1264/)
- (CaRe) Swapnil Gupta, Sreyash Kenkre, Partha Talukdar. "CaRe: Open Knowledge Graph Embeddings". EMNLP/IJCNLP 2019. [*paper*](https://www.aclweb.org/anthology/D19-1036/) [*code*](https://github.com/malllabiisc/CaRE)
- (CPL) Cong Fu, Tong Chen, Meng Qu, Woojeong Jin, Xiang Ren. "Collaborative Policy Learning for Open Knowledge Graph Reasoning". EMNLP/IJCNLP 2019. [*paper*](https://doi.org/10.18653/v1/D19-1269)
- (JoBi) Esma Balkir, Masha Naslidnyk, Dave Palfrey and Arpit Mittal. "Using Pairwise Occurrence Information to Improve Knowledge Graph Completion on Large-Scale Datasets". EMNLP/IJCNLP 2019. [*paper*](https://www.aclweb.org/anthology/D19-1368/)
- (Meta-KGR) Xin Lv, Yuxian Gu, Xu Han, Lei Hou, Juanzi Li, Zhiyuan Liu. "Adapting Meta Knowledge Graph Information for Multi-Hop Reasoning over Few-Shot Relations". EMNLP/IJCNLP 2019. [*paper*](https://doi.org/10.18653/v1/D19-1334)
- (MetaR) Mingyang Chen, Wen Zhang, Wei Zhang, Qiang Chen and Huajun Chen. "Meta Relational Learning for Few-Shot Link Prediction in Knowledge Graphs". EMNLP/IJCNLP 2019. [*paper*](https://www.aclweb.org/anthology/D19-1431/) [*code*](https://github.com/AnselCmy/MetaR)
- (OPTransE) Yao Zhu, Hongzhi Liu, Zhonghai Wu, Yang Song and Tao Zhang. "Representation Learning with Ordered Relation Paths for Knowledge Graph Completion". EMNLP/IJCNLP 2019. [*paper*](https://www.aclweb.org/anthology/D19-1268/)
- (TCVAE) Zihao Wang, Kwunping Lai, Piji Li, Lidong Bing and Wai Lam. "Tackling Long-Tailed Relations and Uncommon Entities in Knowledge Graph Completion". EMNLP/IJCNLP 2019. [*paper*](https://www.aclweb.org/anthology/D19-1024/)
- (TuckER) Ivana Balazevic, Carl Allen, Timothy M. Hospedales. "TuckER: Tensor Factorization for Knowledge Graph Completion". EMNLP/IJCNLP 2019. [*paper*](https://www.aclweb.org/anthology/D19-1522/) [*code*](https://github.com/ibalazevic/TuckER):fire: :boom:

#### UAI

- (EM) Robert Bamler, Farnood Salehi, Stephan Mandt. "Augmenting and Tuning Knowledge Graph Embeddings". UAI 2019. [*paper*](http://auai.org/uai2019/proceedings/papers/172.pdf) [*code*](https://github.com/mandt-lab/knowledge-graph-tuning)
- (MLN) Ondrej Kuzelka, Jesse Davis. "Markov Logic Networks for Knowledge Base Completion: A Theoretical Analysis Under the MCAR Assumption". UAI 2019. [*paper*](http://auai.org/uai2019/proceedings/papers/427.pdf)

#### NAACL

- (CapsE) Dai Quoc Nguyen, Thanh Vu, Tu Dinh Nguyen, Dat Quoc Nguyen, Dinh Q. Phung. "A Capsule Network-based Embedding Model for Knowledge Graph Completion and Search Personalization". NAACL-HLT 2019. [*paper*](https://www.aclweb.org/anthology/N19-1226/) [*code*](https://github.com/daiquocnguyen/CapsE) :fire:
- (ConvR) Xiaotian Jiang, Quan Wang, Bin Wang. "Adaptive Convolution for Multi- Relational Learning". NAACL-HLT 2019. [*paper*](https://www.aclweb.org/anthology/N19-1103/)
- (CRIAGE) Pouya Pezeshkpour, Yifan Tian, Sameer Singh. “Investigating Robustness and Interpretability of Link Prediction via Adversarial Modifications”. NAACL-HLT 2019. [*paper*](https://www.aclweb.org/anthology/N19-1337/) [*code*](https://github.com/pouyapez/criage)
- (FFD) Zihao Fu, Yankai Lin, Zhiyuan Liu, Wai Lam. "Fact Discovery from Knowledge Base via Facet Decomposition". NAACL-HLT 2019. [*paper*](https://www.aclweb.org/anthology/N19-1297/)
- (GRank) Takuma Ebisu, Ryutaro Ichise. "Graph Pattern Entity Ranking Model for Knowledge Graph Completion". NAACL-HLT 2019. [*paper*](https://www.aclweb.org/anthology/N19-1104/)
- (TMKGE) Dingcheng Li, Siamak Zamani, Jingyuan Zhang, Ping Li. "Integration of Knowledge Graph Embedding Into Topic Modeling with Hierarchical Dirichlet Process". NAACL-HLT 2019. [*paper*](https://www.aclweb.org/anthology/N19-1099/)

#### KDD

- (JOIE) Junheng Hao, Muhao Chen, Wenchao Yu, Yizhou Sun, Wei Wang. "Universal Representation Learning of Knowledge Bases by Jointly Embedding Instances and Ontological Concepts". KDD 2019. [*paper*](https://dl.acm.org/doi/10.1145/3292500.3330838) [*code*](https://github.com/JunhengH/joie-kdd19)

#### ICDE

- (NSCaching) Yongqi Zhang, Quanming Yao, Yingxia Shao, Lei Chen. "NSCaching: Simple and Efficient Negative Sampling for Knowledge Graph Embedding". ICDE 2019\. [*paper*](https://ieeexplore.ieee.org/document/8731371) [*code*](https://github.com/yzhangee/NSCaching)

#### WSDM

- (CrossE) Wen Zhang, Bibek Paudel, Wei Zhang, Abraham Bernstein, Huajun Chen. "Interaction Embeddings for Prediction and Explanation in Knowledge Graphs". WSDM 2019. [*paper*](https://dl.acm.org/doi/10.1145/3289600.3291014) [*code*](https://github.com/wencolani/CrossE) :fire:

#### ISWC

- (HapPenIng) Simon Gottschalk, Elena Demidova. "HapPenIng: Happen, Predict, Infer - Event Series Completion in a Knowledge Graph". ISWC 2019. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-30793-6_12)
- (LiteralE) Agustinus Kristiadi, Mohammad Asif Khan, Denis Lukovnikov, Jens Lehmann, Asja Fischer. "Incorporating Literals into Knowledge Graph Embeddings". ISWC 2019. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-30793-6_20) [*code*](https://github.com/SmartDataAnalytics/LiteralE)
- (KEEN) Mehdi Ali, Hajira Jabeen, Charles Tapley Hoyt, Jens Lehmann. "The KEEN Universe - An Ecosystem for Knowledge Graph Embeddings with a Focus on Reproducibility and Transferability". ISWC 2019. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-30796-7_1)
- (RW-LMLM) Changjian Wang, Minghui Yan, Chuanrun Yi, Ying Sha. "Capturing Semantic and Syntactic Information for Link Prediction in Knowledge Graphs". ISWC 2019. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-30793-6_38)
- (TERA) Erik B. Myklebust, Ernesto Jiménez-Ruiz, Jiaoyan Chen, Raoul Wolf, Knut Erik Tollefsen. "Knowledge Graph Embedding for Ecotoxicological Effect Prediction". ISWC 2019. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-30796-7_30)
- (TransEdge) Zequn Sun, JiaCheng Huang, Wei Hu, Muhao Chen, Lingbing Guo, Yuzhong Qu. "TransEdge: Translating Relation-Contextualized Embeddings for Knowledge Graphs". ISWC 2019. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-30793-6_35)

#### ESWC

- (CNN) Sébastien Ferré. "Link Prediction in Knowledge Graphs with Concepts of Nearest Neighbours". ESWC 2019. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-21348-0_6)
- (MMKG) Ye Liu, Hui Li, Alberto García-Durán, Mathias Niepert, Daniel O?oro-Rubio, David S. Rosenblum. "MMKG: Multi-modal Knowledge Graphs". ESWC 2019. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-21348-0_30)

#### WWW

- (ActiveLink) Natalia Ostapuk, Jie Yang, Philippe Cudré-Mauroux. "ActiveLink: Deep Active Learning for Link Prediction in Knowledge Graphs". WWW 2019. [*paper*](https://dl.acm.org/doi/10.1145/3308558.3313620) [*code*](https://github.com/eXascaleInfolab/ActiveLink)
- (IterE) Wen Zhang, Bibek Paudel, Liang Wang, Jiaoyan Chen, Hai Zhu, Wei Zhang, Abraham Bernstein, Huajun Chen. "Iteratively Learning Embeddings and Rules for Knowledge Graph Reasoning". WWW 2019. [*paper*](https://dl.acm.org/doi/10.1145/3308558.3313612) [*code*](https://github.com/wencolani/IterE) :fire:
- (MARINE) Ming-Han Feng, Chin-Chi Hsu, Cheng-Te Li, Mi-Yen Yeh, Shou-De Lin. "MARINE: Multi-relational Network Embeddings with Relational Proximity and Node Attributes". WWW 2019. [*paper*](https://dl.acm.org/doi/10.1145/3308558.3313715)
- (NaLP) Saiping Guan, Xiaolong Jin, Yuanzhuo Wang, Xueqi Cheng. "Link Prediction on N-ary Relational Data". WWW 2019. [*paper*](https://dl.acm.org/doi/10.1145/3308558.3313414) [*code*](https://github.com/gsp2014/NaLP)
- (KTUP) Yixin Cao, Xiang Wang, Xiangnan He, Zikun Hu, Tat-Seng Chua. "Unifying Knowledge Graph Learning and Recommendation: Towards a Better Understanding of User Preferences". WWW 2019. [*paper*](https://dl.acm.org/doi/10.1145/3308558.3313705)

#### ICASSP

- (GRNN) Vassilis N. Ioannidis, Antonio G. Marques, Georgios B. Giannakis. "A Recurrent Graph Neural Network for Multi-relational Data". ICASSP 2019. [*paper*](https://ieeexplore.ieee.org/document/8682836)

## 2020

### Journal

#### Information Sciences

- (FGEM) Richong Zhang, Yongyi Mao, Weihua Zhao. "Knowledge graphs completion via probabilistic reasoning". Information Sciences 2020. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0020025520300918?via%3Dihub)
- (MAKR) Yongming Han, GuoFei Chen, Zhongkun Li, Zhiqiang Geng, Fang Li, Bo Ma. "An asymmetric knowledge representation learning in manifold space". Information Sciences 2020. [*paper*](https://doi.org/10.1016/j.ins.2020.04.036)

#### IEEE Transactions on Knowledge and Data Engineering

- (KGLG) Takuma Ebisu, Ryutaro Ichise. "Generalized Translation-Based Embedding of Knowledge Graph". IEEE Transactions on Knowledge and Data Engineering 2020. [*paper*](https://doi.org/10.1109/TKDE.2019.2893920)

#### Expert Systems with Applications

- Batselem Jagvaral, Wan-Kon Lee, Jae-Seung Roh, Min-Sung Kim, Young-Tack Park."Path-based reasoning approach for knowledge graph completion using CNNBiLSTM with attention mechanism". Expert Systems with Applications 2020. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0957417419306785?via%3Dihub)
- (SDT) Xiaojun Chen, Shengbin Jia, Ling Ding, Hong Shen, Yang Xiang. "SDT: An integrated model for open-world knowledge graph reasoning". Expert Systems with Applications 2020. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0957417420306904?via%3Dihub)

#### Knowledge Based Systems

- (ADRL) Qi Wang, Yongsheng Hao, Jie Cao. "ADRL: An attention-based deep reinforcement learning framework for knowledge graph reasoning". Knowledge Based Systems 2020. [*paper*](https://doi.org/10.1016/j.knosys.2020.105910)
- (ConnectE) Yu Zhao, Anxiang Zhang, Huali Feng, Qing Li, Patrick Gallinari, Fuji Ren. "Knowledge graph entity typing via learning connecting embeddings". Knowledge Based Systems 2020. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705120301921?via%3Dihub)
- (GRL) Qi Wang, Yuede Ji, Yongsheng Hao, Jie Cao. "GRL: Knowledge graph completion with GAN-based reinforcement learning". Knowledge Based Systems 2020. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705120305505?via%3Dihub)
- (TransE&RW) Chen Li, Xutan Peng, Shanghang Zhang, Hao Peng, Philip S. Yu, Min He, Linfen g Du, Lihong Wang. "Modeling relation paths for knowledge base completion via joint adversarial training". Knowledge Based Systems 2020. [*paper*](https://doi.org/10.1016/j.knosys.2020.105865)
- (WDGAN) Yuanfei Dai, Shiping Wang, Xing Chen, Chaoyang Xu, Wenzhong Guo. "Generative adversarial networks based on Wasserstein distance for knowledge graph embeddings". Knowledge Based Systems 2020. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705119305143?via%3Dihub)

#### Neurocomputing

- (ALSTM) Qi Wang , Yongsheng Hao. "ALSTM: An attention-based long short-term memory framework for knowledge base reasoning". Neurocomputing 2020. [*paper*](https://doi.org/10.1016/j.neucom.2020.02.065)

#### Data Mining and Knowledge Discovery

- (Semi-supervised) Jia Zhu, Zetao Zheng, Min Yang, Gabriel Pui Cheong Fung, Yong Tang. "A semi-supervised model for knowledge graph embedding". Data Mining and Knowledge Discovery 2020. [*paper*](https://link.springer.com/article/10.1007/s10618-019-00653-z)

#### Neural Computing and Applications

- (NKSGAN) Hai Liu, Kairong Hu, Fu Lee Wang, Tianyong Hao. "Aggregating neighborhood information for negative sampling for knowledge graph embedding". Neural Computing and Applications 2020. [*paper*](https://link.springer.com/article/10.1007%2Fs00521-020-04940-5)
- (PRCTA) Kai Lei, Jin Zhang, Yuexiang Xie, Desi Wen, Daoyuan Chen, Min Yang, Ying Shen. "Path-based reasoning with constrained type attention for knowledge graph completion". Neural Computing and Applications 2020. [*paper*](https://link.springer.com/article/10.1007%2Fs00521-019-04181-1)

#### Applied Intelligence

- (CILKBC) Hongbin Wang, Shengchen Jiang, Zhengtao Yu. "Modeling of complex internal logic for knowledge base completion". Applied Intelligence 2020. [*paper*](https://link.springer.com/article/10.1007/s10489-020-01734-z)

### Conference

#### ICLR

- (Calibration) Pedro Tabacof, Luca Costabello. "Probability Calibration for Knowledge Graph Embedding Models". ICLR 2020. [*paper*](https://openreview.net/forum?id=S1g8K1BFwS)
- (CompGCN) Shikhar Vashishth, Soumya Sanyal, Vikram Nitin, Partha Talukdar. "Composition-based Multi-Relational Graph Convolutional Networks". ICLR 2020. [*paper*](https://openreview.net/forum?id=BylA_C4tPr) [*code*](https://github.com/malllabiisc/CompGCN) :fire:
- (DPMPN) Xiaoran Xu, Wei Feng, Yunsheng Jiang, Xiaohui Xie, Zhiqing Sun, Zhi-Hong Deng. "Dynamically Pruned Message Passing Networks for Large-scale Knowledge Graph Reasoning". ICLR 2020. [*paper*](https://openreview.net/forum?id=rkeuAhVKvB) [*code*](https://github.com/netpaladinx/DPMPN)
- (DrKIT) Bhuwan Dhingra, Manzil Zaheer, Vidhisha Balachandran, Graham Neubig, Ruslan Salakhutdinov, William W. Cohen. "Differentiable Reasoning over a Virtual Knowledge Base". ICLR 2020. [*paper*](https://openreview.net/forum?id=SJxstlHFPH) [*code*](https://github.com/google-research/language/tree/master/language/labs/drkit) :fire:
- (Neural-LP-N) Po-Wei Wang, Daria Stepanova, Csaba Domokos, J. Zico Kolter. "Differentiable learning of numerical rules in knowledge graphs". ICLR 2020. [*paper*](https://openreview.net/forum?id=rJleKgrKwS)
- (Q2B) Hongyu Ren, Weihua Hu, Jure Leskovec. "Query2box: Reasoning over Knowledge Graphs in Vector Space Using Box Embeddings". ICLR 2020. [*paper*](https://openreview.net/forum?id=BJgr4kSFDS) [*code*](https://github.com/hyren/query2box) :fire:
- (ReifKB) William W. Cohen, Haitian Sun, R. Alex Hofer, Matthew Siegler. "Scalable Neural Methods for Reasoning With a Symbolic Knowledge Base". ICLR 2020. [*paper*](https://openreview.net/forum?id=BJlguT4YPr)
- (TComplEx) Timothée Lacroix, Guillaume Obozinski, Nicolas Usunier. "Tensor Decompositions for Temporal Knowledge Base Completion". ICLR 2020. [*paper*](https://openreview.net/forum?id=rke2P1BFwS) [*code*](https://github.com/facebookresearch/tkbc)
- (Teach) Daniel Ruffinelli, Samuel Broscheit, Rainer Gemulla. "You CAN Teach an Old Dog New Tricks! On Training Knowledge Graph Embeddings". ICLR 2020. [*paper*](https://openreview.net/forum?id=BkxSmlBFvr) [*code*](https://github.com/uma-pi1/kge) :fire:

#### AAAI

- (CoPER) George Stoica, Otilia Stretcu, Anthony Platanios, Tom Mitchell, Barnabas Poczos. "Contextual Parameter Generation for Knowledge Graph Link Prediction". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5693) [*code*](https://github.com/otiliastr/coper)

- (DE-SimplE) Rishab Goel, Seyed Mehran Kazemi, Marcus Brubaker, Pascal Poupart. "Diachronic Embedding for Temporal Knowledge Graph Completion". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5815) [*code*](https://github.com/BorealisAI/DE-SimplE) :fire:
- (EvolveGCN) Aldo Pareja, Giacomo Domeniconi, Jie Chen, Tengfei Ma, Toyotaro Suzumura, Hiroki Kanezashi, Tim Kaler, Tao B. Schardl, Charles E. Leiserson. "EvolveGCN: Evolving Graph Convolutional Networks for Dynamic Graphs". AAAI 2020. [*paper*](https://ojs.aaai.org//index.php/AAAI/article/view/5984)
- (FSRL) Chuxu Zhang, Huaxiu Yao, Chao Huang, Meng Jiang, Zhenhui Li, Nitesh V. Chawla. "Few-Shot Knowledge Graph Completion". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5698) [*code*](https://github.com/chuxuzhang/AAAI2020_FSRL)
- (GNTPs) Pasquale Minervini, Matko Bosnjak, Tim Rocktäschel, Sebastian Riedel, Edward Grefenstette. "Differentiable Reasoning on Large Knowledge Bases and Natural Language". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5962) :fire:
- (HAKE) Zhanqiu Zhang, Jianyu Cai, Yongdong Zhang, Jie Wang. "Learning Hierarchy-Aware Knowledge Graph Embeddings for Link Prediction". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5701) [*code*](https://github.com/MIRALab-USTC/KGE-HAKE) :fire:
- (InteractE) Shikhar Vashishth, Soumya Sanyal, Vikram Nitin, Nilesh Agrawal, Partha Talukdar. "InteractE: Improving Convolution-based Knowledge Graph Embeddings by Increasing Feature Interactions". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5694) [*code*](https://github.com/malllabiisc/InteractE) [*supp*](https://shikhar-vashishth.github.io/assets/pdf/interacte_supp.pdf) :fire:
- (ParamE) Feihu Che, Dawei Zhang, Jianhua Tao, Mingyue Niu, Bocheng Zhao. "ParamE: Regarding Neural Network Parameters as Relation Embeddings for Knowledge Graph Completion". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5665)
- (R2D2) Marcel Hildebrandt, Jorge Andres Quintero Serna, Yunpu Ma, Martin Ringsquandl, Mitchell Joblin, Volker Tresp. "Reasoning on Knowledge Graphs with Debate Dynamics". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/6600) [*code*](https://github.com/m-hildebrandt/R2D2)
- (RARL) Giuseppe Pirr . "Relatedness and TBox-Driven Rule Learning in Large Knowledge Bases". AAAI 2020. [*paper*](https://ojs.aaai.org//index.php/AAAI/article/view/5690)
- (RGHAT) Zhao Zhang, Fuzhen Zhuang, Hengshu Zhu, Zhiping Shi, Hui Xiong, Qing He. "Relational Graph Neural Network with Hierarchical Attention for Knowledge Graph Completion". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/6508)
- (Robust) Peru Bhardwaj. "Towards Adversarially Robust Knowledge Graph Embeddings". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/7128)
- (RPJE) Guanglin Niu, Yongfei Zhang, Bo Li, Peng Cui, Si Liu, Jingyang Li, Xiaowei Zhang. "Rule-Guided Compositional Representation Learning on Knowledge Graphs". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5687) [*code*](https://github.com/ngl567/RPJE)
- (SimE) Chaitanya Malaviya, Chandra Bhagavatula, Antoine Bosselut, Yejin Choi. "Commonsense Knowledge Base Completion with Structural and Semantic Context". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/5684) :fire:
- (Triple2Vec) Valeria Fionda, Giuseppe Pirr . "Learning Triple Embeddings from Knowledge Graphs". AAAI 2020. [*paper*](https://ojs.aaai.org//index.php/AAAI/article/view/5800)
- (ZSGAN) Pengda Qin, Xin Wang, Wenhu Chen, Chunyun Zhang, Weiran Xu, William Yang Wang. "Generative Adversarial Zero-Shot Relational Learning for Knowledge Graphs". AAAI 2020. [*paper*](https://aaai.org/ojs/index.php/AAAI/article/view/6392) [*code*](https://github.com/Panda0406/Zero-shot-knowledge-graph-relational-learning)

#### NeurIPS

- (BETAE) Hongyu Ren, Jure Leskovec. "Beta Embeddings for Multi-Hop Logical Reasoning in Knowledge Graphs". NeurIPS 2020. [*paper*](https://proceedings.neurips.cc/paper/2020/hash/e43739bba7cdb577e9e3e4e42447f5a5-Abstract.html) [*code*](http://snap.stanford.edu/betae/)
- (BoxE) Ralph Abboud, Ismail Ilkan Ceylan, Thomas Lukasiewicz, Tommaso Salvatori. "BoxE: A Box Embedding Model for Knowledge Base Completion". NeurIPS 2020. [*paper*](https://proceedings.neurips.cc/paper/2020/hash/6dbbe6abe5f14af882ff977fc3f35501-Abstract.html)
- (DURA) Zhanqiu Zhang, Jianyu Cai, Jie Wang. "Duality-Induced Regularizer for Tensor Factorization Based Knowledge Graph Completion". NeurIPS 2020. [*paper*](https://proceedings.neurips.cc/paper/2020/hash/f6185f0ef02dcaec414a3171cd01c697-Abstract.html) [*code*](https://github.com/MIRALab-USTC/KGE-DURA)
- (EmQL) Haitian Sun, Andrew O. Arnold, Tania Bedrax-Weiss, Fernando Pereira, William W. Cohen. "Faithful Embeddings for Knowledge Base Queries". NeurIPS 2020. [*paper*](https://proceedings.neurips.cc/paper/2020/hash/fe74074593f21197b7b7be3c08678616-Abstract.html)
- (GEN) Jinheon Baek, Dong Bok Lee, Sung Ju Hwang. "Learning to Extrapolate Knowledge: Transductive Few-shot Out-of-Graph Link Prediction". NeurIPS 2020. [*paper*](https://neurips.cc/virtual/2020/public/poster_0663a4ddceacb40b095eda264a85f15c.html) [*code*](https://github.com/JinheonBaek/GEN)
- (Interstellar) Yongqi Zhang, Quanming Yao, Lei Chen. "Interstellar: Searching Recurrent Architecture for Knowledge Graph Embedding". NeurIPS 2020. [*paper*](https://proceedings.neurips.cc/paper/2020/hash/722caafb4825ef5d8670710fa29087cf-Abstract.html) [*code*](https://github.com/AutoML-4Paradigm/Interstellar)

#### ACL

- (ATTH) Ines Chami, Adva Wolf, Da-Cheng Juan, Frederic Sala, Sujith Ravi and Christopher Ré. "Low-Dimensional Hyperbolic Knowledge Graph Embeddings". ACL 2020. [*paper*](https://www.aclweb.org/anthology/2020.acl-main.617/) [*code*](https://github.com/HazyResearch/KGEmb)
- (Compression) Mrinmaya Sachan. "Knowledge Graph Embedding Compression". ACL 2020. [*paper*](https://www.aclweb.org/anthology/2020.acl-main.238/)
- (ConnectE) Yu Zhao, anxiang zhang, Ruobing Xie, Kang Liu and Xiaojie WANG. "Connecting Embeddings for Knowledge Graph Entity Typing". ACL 2020. [*paper*](https://www.aclweb.org/anthology/2020.acl-main.572/) [*code*](https://github.com/Adam1679/ConnectE)
- (NeuInfer) Saiping Guan, Xiaolong Jin, Jiafeng Guo, Yuanzhuo Wang, Xueqi Cheng. "NeuInfer: Knowledge Inference on N-ary Facts". ACL 2020. [*paper*](https://aclanthology.org/2020.acl-main.546/)
- (OLP) Samuel Broscheit, Kiril Gashteovski, Yanjie Wang, Rainer Gemulla. "Can We Predict New Facts with Open Knowledge Graph Embeddings? A Benchmark for Open Link Prediction". ACL 2020. [*paper*](https://www.aclweb.org/anthology/2020.acl-main.209/) [*code*](https://github.com/samuelbroscheit/open_knowledge_graph_embeddings)
- (OTE) Yun Tang, Jing Huang, Guangtao Wang, Xiaodong He, Bowen Zhou. "Orthogonal Relation Transforms with Graph Context Modeling for Knowledge Graph Embedding". ACL 2020. [*paper*](https://www.aclweb.org/anthology/2020.acl-main.241/) [*code*](https://github.com/JD-AI-Research-Silicon-Valley/KGEmbedding-OTE)
- (Re-evaluation) Zhiqing Sun, Shikhar Vashishth, Soumya Sanyal, Partha Talukdar and Yiming Yang. "A Re-evaluation of Knowledge Graph Completion Methods". ACL 2020. [*paper*](https://www.aclweb.org/anthology/2020.acl-main.489/) [*code*](https://github.com/svjan5/kg-reeval) :fire:
- (ReInceptionE) Zhiwen Xie, Guangyou Zhou, Jin Liu and Jimmy Xiangji Huang. "ReInceptionE: Relation-Aware Inception Network with Joint Local-Global Structural Information for Knowledge Graph Embedding". ACL 2020. [*paper*](https://www.aclweb.org/anthology/2020.acl-main.526/) [*code*](https://github.com/JuneTse/ReInceptionE)
- (SEEK) Wentao Xu, Shun Zheng, Liang He, Bin Shao, Jian Yin and Tie-Yan Liu. "SEEK: Segmented Embedding of Knowledge Graphs". ACL 2020. [*paper*](https://www.aclweb.org/anthology/2020.acl-main.358/) [*code*](https://github.com/Wentao-Xu/SEEK)

#### ICML

- (GraIL) Komal K. Teru, Etienne Denis, Will Hamilton. "Inductive Relation Prediction by Subgraph Reasoning". ICML 2020. [*paper*](http://proceedings.mlr.press/v119/teru20a.html)
- (LowFER) Saadullah Amin, Stalin Varanasi, Katherine Ann Dunfield, Günter Neumann. "LowFER: Low-rank Bilinear Pooling for Link Prediction". ICML 2020. [*paper*](http://proceedings.mlr.press/v119/amin20a) [*code*](https://github.com/suamin/LowFER)

#### IJCAI

- (DArtNet) Sankalp Garg, Navodita Sharma, Woojeong Jin, Xiang Ren. "Temporal Attribute Prediction via Joint Modeling of Multi-Relational Structure Evolution". IJCAI 2020. [*paper*](https://www.ijcai.org/Proceedings/2020/386) [*code*](https://github.com/INK-USC/DArtNet)
- (HypE) Bahare Fatemi, Perouz Taslakian, David Vázquez, David Poole. "Knowledge Hypergraphs: Prediction Beyond Binary Relations". IJCAI 2020. [*paper*](https://www.ijcai.org/Proceedings/2020/303) [*code*](https://github.com/baharefatemi/HypE)
- (RLH) Guojia Wan, Shirui Pan, Chen Gong, Chuan Zhou, Gholamreza Haffari. "Reasoning Like Human: Hierarchical Reinforcement Learning for Knowledge Graph Reasoning". IJCAI 2020. [*paper*](https://www.ijcai.org/proceedings/2020/267)
- (TransRHS) Fuxiang Zhang, Xin Wang, Zhao Li, Jianxin Li. "TransRHS: A Representation Learning Method for Knowledge Graphs with Relation Hierarchical Structure". IJCAI 2020. [*paper*](https://doi.org/10.24963/ijcai.2020/413) [*code*](https://github.com/tjuzhangfx/TransRHS)

#### EMNLP

- (AutoETER) Guanglin Niu, Bo Li, Yongfei Zhang, Shiliang Pu, Jingyang Li. "AutoETER: Automated Entity Type Representation with Relation-Aware Attention for Knowledge Graph Embedding". EMNLP (Findings) 2020. [*paper*](https://www.aclweb.org/anthology/2020.findings-emnlp.105/) [*code*](https://github.com/ngl567/AutoETER)
- (B-CP) Katsuhiko Hayashi, Koki Kishimoto, Masashi Shimbo. "A Greedy Bit-flip Training Algorithm for Binarized Knowledge Graph Embeddings". EMNLP (Findings) 2020. [*paper*](https://www.aclweb.org/anthology/2020.findings-emnlp.10/)
- (CoDEx) Tara Safavi, Danai Koutra. "CoDEx: A Comprehensive Knowledge Graph Completion Benchmark". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.669/)
- (Confidence) JTara Safavi, Danai Koutra, Edgar Meij. "Evaluating the Calibration of Knowledge Graph Embeddings for Trustworthy Link Prediction". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.667/)
- (DA+CSTR) Zhenjie Zhao, Evangelos E. Papalexakis, Xiaojuan Ma. "Learning Physical Common Sense as Knowledge Graph Completion via BERT Data Augmentation and Constrained Tucker Factorization". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.266/)
- (DacKGR) Xin Lv, Xu Han, Lei Hou, Juanzi Li, Zhiyuan Liu, Wei Zhang, Yichi Zhang, Hao Kong, Suhui Wu. "Dynamic Anticipation and Completion for Multi-Hop Reasoning over Sparse Knowledge Graph". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.667/) [*code*](https://github.com/THU-KEG/DacKGR)
- (DebiasE) Joseph Fisher, Arpit Mittal, Dave Palfrey, Christos Christodoulopoulos. "Debiasing knowledge graph embeddings". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.595/)
- (DualTKB) Pierre L. Dognin, Igor Melnyk, Inkit Padhi, Cícero Nogueira dos Santos, Payel Das. "DualTKB: A Dual Learning Bridge between Text and Knowledge Base". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.694/)
- (DyERNIE) Zhen Han, Peng Chen, Yunpu Ma, Volker Tresp. "DyERNIE: Dynamic Evolution of Riemannian Manifold Embeddings for Temporal Knowledge Graph Completion". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.593/)
- (FAAN) Jiawei Sheng, Shu Guo, Zhenyu Chen, Juwei Yue, Lihong Wang, Tingwen Liu, Hongbo Xu. "Adaptive Attentional Network for Few-Shot Knowledge Graph Completion". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.131/) [*code*](https://github.com/JiaweiSheng/FAAN)
- (FIRE) Chuxu Zhang, Lu Yu, Mandana Saebi, Meng Jiang, Nitesh V. Chawla. "FewShot Multi-Hop Relation Reasoning over Knowledge Bases". EMNLP (Findings) 2020. [*paper*](https://www.aclweb.org/anthology/2020.findings-emnlp.51/)
- (HyperKA) Zequn Sun, Muhao Chen, Wei Hu, Chengming Wang, Jian Dai, Wei Zhang. "Knowledge Association with Hyperbolic Knowledge Graph Embeddings". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.460/) [*code*](https://github.com/nju-websoft/HyperKA)
- (KEnS) Xuelu Chen, Muhao Chen, Changjun Fan, Ankith Uppunda, Yizhou Sun, Carlo Zaniolo. "Multilingual Knowledge Graph Completion via Ensemble Knowledge Transfer". EMNLP (Findings) 2020. [*paper*](https://www.aclweb.org/anthology/2020.findings-emnlp.290/)
- (MCMH) Lu Zhang, Mo Yu, Tian Gao, Yue Yu. "MCMH: Learning Multi-Chain MultiHop Rules for Knowledge Graph Reasoning". EMNLP (Findings) 2020. [*paper*](https://www.aclweb.org/anthology/2020.findings-emnlp.351/)
- (oDistMult) Marjan Albooyeh, Rishab Goel, Seyed Mehran Kazemi. "Out-of-Sample Representation Learning for Knowledge Graphs". EMNLP (Findings) 2020. [*paper*](https://www.aclweb.org/anthology/2020.findings-emnlp.241/)
- (PCBR) Rajarshi Das, Ameya Godbole, Nicholas Monath, Manzil Zaheer, Andrew McCallum. "Probabilistic Case-based Reasoning in Knowledge Bases". EMNLP (Findings) 2020. [*paper*](https://aclanthology.org/2020.findings-emnlp.427/)
- (Pretrain-KGE) Zhiyuan Zhang, Xiaoqian Liu, Yi Zhang, Qi Su, Xu Sun, Bin He. "Pretrain-KGE: Learning Knowledge Representation from Pretrained Language Models". EMNLP (Findings) 2020. [*paper*](https://aclanthology.org/2020.findings-emnlp.25/)
- (RE-NET) Woojeong Jin, Meng Qu, Xisen Jin, Xiang Ren. "Recurrent Event Network: Autoregressive Structure Inferenceover Temporal Knowledge Graphs". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.541/) [*code*](https://github.com/INK-USC/RE-Net)
- (RuleGuider) Deren Lei, Gangrong Jiang, Xiaotao Gu, Kexuan Sun, Yuning Mao, Xiang Ren. "Learning Collaborative Agents with Rule Guidance for Knowledge Graph Reasoning". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.688/)
- (SANS) Kian Ahrabian, Aarash Feizi, Yasmin Salehi, William L. Hamilton, Avishek Joey Bose. "Structure Aware Negative Sampling in Knowledge Graphs". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.492/)
- (STARE) Mikhail Galkin, Priyansh Trivedi, Gaurav Maheshwari, Ricardo Usbeck, Jens Lehmann. "Message Passing for Hyper-Relational Knowledge Graphs". EMNLP 2020\. [*paper*](https://aclanthology.org/2020.emnlp-main.596/)
- (TeMP) Jiapeng Wu, Meng Cao, Jackie Chi Kit Cheung, William L. Hamilton. "TeMP: Temporal Message Passing for Temporal Knowledge Graph Completion". EMNLP 2020\. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.462/) [*code*](https://github.com/JiapengWu/TeMP)
- (TIMEPLEX) Prachi Jain, Sushant Rathi, Mausam, Soumen Chakrabarti. "Temporal Knowledge Base Completion: New Algorithms and Evaluation Protocols". EMNLP 2020. [*paper*](https://www.aclweb.org/anthology/2020.emnlp-main.305/) [*code*](https://github.com/dair-iitd/tkbi)

#### ECAI

- (BTDE) Tao Luo, Yifan Wei, Mei Yu, Xuewei Li, Mankun Zhao, Tianyi Xu, Jian Yu, Jie Gao, Ruiguo Yu. "BTDE: Block Term Decomposition Embedding for Link Prediction in Knowledge Graph". ECAI 2020. [*paper*](http://ebooks.iospress.nl/publication/54966)
- (HALF) Meng Wang, Tongtong Wu, Guilin Qi. "A Hash Learning Framework for Search-Oriented Knowledge Graph Embedding". ECAI 2020. [*paper*](http://ebooks.iospress.nl/publication/54979)
- (MDE) Afshin Sadeghi, Damien Graux, Hamed Shariat Yazdi, Jens Lehmann. "MDE: Multiple Distance Embeddings for Link Prediction in Knowledge Graphs". ECAI 2020. [*paper*](http://ebooks.iospress.nl/publication/55043) [*code*](https://github.com/mlwin-de/MDE)
- (MEI) Hung Nghiep Tran, Atsuhiro Takasu. "Multi-Partition Embedding Interaction with Block Term Format for Knowledge Graph Completion". ECAI 2020. [*paper*](http://ebooks.iospress.nl/publication/54979) [*code*](https://github.com/tranhungnghiep/AnalyzeKGE)

#### COLING

- (AcrE) Feiliang Ren, Juchen Li, Huihui Zhang, Shilei Liu, Bochao Li, Ruicheng Ming, Yujia Bai. "Knowledge Graph Embedding with Atrous Convolution and Residual Learning". COLING 2020. [*paper*](https://www.aclweb.org/anthology/2020.coling-main.134/) [*code*](https://github.com/neukg/AcrE)
- (AprilE) Yuzhang Liu, Peng Wang, Yingtai Li, Yizhan Shao, Zhongkai Xu. "AprilE: Attention with Pseudo Residual Connection for Knowledge Graph Embedding". COLING 2020. [*paper*](https://www.aclweb.org/anthology/2020.coling-main.44/)
- (GeomE) Chengjin Xu, Mojtaba Nayyeri, Yung-Yu Chen, Jens Lehmann. "Knowledge Graph Embeddings in Geometric Algebras". COLING 2020. [*paper*](https://www.aclweb.org/anthology/2020.coling-main.46/)
- (IntKB) Bernhard Kratzwald, Guo Kunpeng, Stefan Feuerriegel, Dennis Diefenbach. "IntKB: A Verifiable Interactive Framework for Knowledge Base Completion". COLING 2020. [*paper*](https://www.aclweb.org/anthology/2020.coling-main.490/)
- (KD-MKB) Raphaël Sourty, Jose G. Moreno, François-Paul Servant, Lynda TamineLechani. "Knowledge Base Embedding By Cooperative Knowledge Distillation". COLING 2020. [*paper*](https://aclanthology.org/2020.coling-main.489/)
- (KG-BERT) Bosung Kim, Taesuk Hong, Youngjoong Ko, Jungyun Seo. "Multi-Task Learning for Knowledge Graph Completion with Pre-trained Language Models". COLING 2020. [*paper*](https://www.aclweb.org/anthology/2020.coling-main.153/)
- (RatE) Hao Huang, Guodong Long, Tao Shen, Jing Jiang, Chengqi Zhang. "RatE: Relation-Adaptive Translating Embedding for Knowledge Graph Completion". COLING 2020. [*paper*](https://www.aclweb.org/anthology/2020.coling-main.48/)
- (TeRo) Chengjin Xu, Mojtaba Nayyeri, Fouad Alkhoury, Hamed Shariat Yazdi, Jens Lehmann. "TeRo: A Time-aware Knowledge Graph Embedding via Temporal Rotation". COLING 2020. [*paper*](https://www.aclweb.org/anthology/2020.coling-main.139/) [*code*](https://github.com/soledad921/ATISE)

#### UAI

- (Strat-Hits) Aisha Mohamed, Shameem Puthiya Parambath, Zoi Kaoudi, Ashraf Aboulnaga. "Popularity Agnostic Evaluation of Knowledge Graph Embeddings". UAI 2020. [*paper*](http://proceedings.mlr.press/v124/mohamed20a.html)
- (TRACTOR) Tal Friedman, Guy Van den Broeck. "Symbolic Querying of Vector Spaces: Probabilistic Databases Meets Relational Embeddings". UAI 2020. [*paper*](http://proceedings.mlr.press/v124/friedman20a.html)

#### AAMAS

- (TransL) Zeyuan Cui, Shijun Liu, Li Pan, Qiang He. "Translating Embedding with Local Connection for Knowledge Graph Completion". AAMAS 2020. [*paper*](https://dl.acm.org/doi/abs/10.5555/3398761.3398995) [*code*](https://github.com/KGCompletion/TransL)

#### SIGMOD

- (FMRR) Farahnaz Akrami, Mohammed Samiul Saeef, Qingheng Zhang, Wei Hu, Chengkai Li. "Realistic Re-evaluation of Knowledge Graph Completion Methods: An Experimental Study". SIGMOD 2020. [*paper*](https://dl.acm.org/doi/10.1145/3318464.3380599)

#### ICDE

- (AutoSF) Yongqi Zhang, Quanming Yao, Wenyuan Dai, Lei Chen. "AutoSF: Searching Scoring Functions for Knowledge Graph Embedding". ICDE 2020. [*paper*](https://doi.org/10.1109/ICDE48307.2020.00044) [*code*](https://github.com/yzhangee/AutoSF)

#### SIGIR

- (DGL-KE) Da Zheng, Xiang Song, Chao Ma, Zeyuan Tan, Zihao Ye, Jin Dong, Hao Xiong, Zheng Zhang, George Karypis. "DGL-KE: Training Knowledge Graph Embeddings at Scale". SIGIR 2020. [*paper*](https://dl.acm.org/doi/10.1145/3397271.3401172) [*code*](https://github.com/awslabs/dgl-ke)

#### CIKM

- (ELP) Russa Biswas. "Embedding based Link Prediction for Knowledge Graph Completion". CIKM 2020. [*paper*](https://dl.acm.org/doi/10.1145/3340531.3418512)
- (GAEAT) Yanfei Han, Quan Fang, Jun Hu, Shengsheng Qian, Changsheng Xu. "GAEAT: Graph Auto-Encoder Attention Networks for Knowledge Graph Completion". CIKM 2020. [*paper*](https://dl.acm.org/doi/10.1145/3340531.3412148)
- (LCWA) Iti Bansal, Sudhanshu Tiwari, Carlos R. Rivero. "The Impact of Negative Triple Generation Strategies and Anomalies on Knowledge Graph Completion". CIKM 2020. [*paper*](https://dl.acm.org/doi/10.1145/3340531.3412023) [*code*](https://github.com/crrivero/ImpactNegativeTriples)
- (NagE) Tong Yang, Long Sha, Pengyu Hong. "NagE: Non-Abelian Group Embedding for Knowledge Graphs". CIKM 2020. [*paper*](https://dl.acm.org/doi/10.1145/3340531.3411875)
- (NASE) Xiaoyu Kou, Bingfeng Luo, Huang Hu, Yan Zhang. "NASE: Learning Knowledge Graph Embedding for Link Prediction via Neural Architecture Search". CIKM 2020. [*paper*](https://dl.acm.org/doi/10.1145/3340531.3412104) [*code*](https://github.com/KXY-PUBLIC/NASE)
- (Rotate3D) Chang Gao, Chengjie Sun, Lili Shan, Lei Lin, Mingjiang Wang. "Rotate3D: Representing Relations as Rotations in Three-Dimensional Space for Knowledge Graph Embedding". CIKM 2020. [*paper*](https://dl.acm.org/doi/10.1145/3340531.3411889) [*code*](https://github.com/gao-xiao-bai/Rotate3D-Representing-Relations-as-Rotations-in-Three-Dimensional-Space-for-KG-Embedding)
- (SLRE) Shu Guo, Lin Li, Zhen Hui, Lingshuai Meng, Bingnan Ma, Wei Liu, Lihong Wang, Haibin Zhai, Hong Zhang. "Knowledge Graph Embedding Preserving Soft Logical Regularity". CIKM 2020. [*paper*](https://dl.acm.org/doi/10.1145/3340531.3412055) [*code*](https://github.com/StudyGroup-lab/SLRE)
- (ToKE) Julien Leblay, Melisachew Wudage Chekol, Xin Liu. "Towards Temporal Knowledge Graph Embeddings with Arbitrary Time Precision". CIKM 2020. [*paper*](https://dl.acm.org/doi/10.1145/3340531.3412028) [*code*](https://gitlab.com/jleblay/tokei)

#### DASFAA

- (PDKE) Sicong Dong, Xin Wang, Lele Chai, Jianxin Li, Yajun Yang. "PDKE: An Efficient Distributed Embedding Framework for Large Knowledge Graphs". DASFAA 2020. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-59416-9_35)

#### ISWC

- (ATiSE) Chenjin Xu, Mojtaba Nayyeri, Fouad Alkhoury, Hamed Shariat Yazdi, Jens Lehmann. "Temporal Knowledge Graph Completion Based on Time Series Gaussian Embedding". ISWC 2020. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-62419-4_37) [*code*](https://github.com/soledad921/ATISE)
- (BCRL) Gang Wu, Wenfang Wu, Leilei Li, Guodong Zhao, Donghong Han, Baiyou Qiao. "BCRL: Long Text Friendly Knowledge Graph Representation Learning". ISWC 2020. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-62419-4_36)
- (IELP) Rajarshi Bhowmik, Gerard de Melo. "Explainable Link Prediction for Emerging Entities in Knowledge Graphs". ISWC 2020. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-62419-4_3) [*code*](https://github.com/kingsaint/InductiveExplainableLinkPrediction)
- (SpacE) Mojtaba Nayyeri, Chengjin Xu, Sahar Vahdati, Nadezhda Vassilyeva, Emanuel Sallinger, Hamed Shariat Yazdi, Jens Lehmann. "Fantastic Knowledge Graph Embeddings and How to Find the Right Space for Them". ISWC 2020. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-62419-4_25)

#### ICDM

- (HybridER) Susheel Suresh, Jennifer Neville. "A Hybrid Model for Learning Embeddings and Logical Rules Simultaneously from Knowledge Graphs". ICDM 2020. [*paper*](https://ieeexplore.ieee.org/document/9338353)
- (LineaRE) Yanhui Peng, Jing Zhang. "LineaRE: Simple but Powerful Knowledge Graph Embedding for Link Prediction". ICDM 2020. [*paper*](https://ieeexplore.ieee.org/document/9338434)

#### ESWC

- (FAMER) Alieh Saeedi, Eric Peukert, Erhard Rahm. "Incremental Multi-source Entity Resolution for Knowledge Graph Completion". ESWC 2020. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-49461-2_23)
- (HyperKG) Prodromos Kolyvakis, Alexandros Kalousis, Dimitris Kiritsis. "Hyperbolic Knowledge Graph Embeddings for Knowledge Base Completion". ESWC 2020.

[*paper*](https://doi.org/10.1007/978-3-030-49461-2_12) [*code*](https://github.com/prokolyvakis/hyperkg)

- (YAGO4) Thomas Pellissier Tanon, Gerhard Weikum, Fabian M. Suchanek. "YAGO 4: A Reason-able Knowledge Base". ESWC 2020. [*paper*](https://doi.org/10.1007/978-3-030-49461-2_34) [*code*](https://github.com/yago-naga/yago4)

#### WWW

- (Curation) Jiaoyan Chen, Xi Chen, Ian Horrocks, Ernesto Jiménez-Ruiz, Erik B. Myklebust. "Correcting Knowledge Base Assertions". WWW 2020. [*paper*](https://dl.acm.org/doi/10.1145/3366423.3380226) [*code*](https://github.com/ChenJiaoyan/KG_Curation)
- (GETD) Yu Liu, Quanming Yao, Yong Li. "Generalizing Tensor Decomposition for Nary Relational Knowledge Bases". WWW 2020. [*paper*](https://dl.acm.org/doi/10.1145/3366423.3380188) [*code*](https://github.com/liuyuaa/GETD)
- (HINGE) Paolo Rosso, Dingqi Yang, Philippe Cudré-Mauroux. "Beyond Triplets: Hyper-Relational Knowledge Graph Embedding for Link Prediction". WWW 2020. [*paper*](https://doi.org/10.1145/3366423.3380257) [*code*](https://github.com/eXascaleInfolab/HINGE_code)
- (Subgraph) Unmesh Joshi, Jacopo Urbani. "Searching for Embeddings in a Haystack: Link Prediction on Knowledge Graphs with Subgraph Pruning". WWW 2020. [*paper*](https://doi.org/10.1145/3366423.3380043)
- (TDGNN) Liang Qu, Huaisheng Zhu, Qiqi Duan, Yuhui Shi. "Continuous-Time Link Prediction via Temporal Dependent Graph Neural Network". WWW 2020. [*paper*](https://dl.acm.org/doi/10.1145/3366423.3380073) [*code*](https://github.com/Leo-Q-316/TDGNN)
- (UPGAN) Gaole He, Junyi Li, Wayne Xin Zhao, Peiju Liu, Ji-Rong Wen. "Mining Implicit Entity Preference from User-Item Interaction Data for Knowledge Graph Completion via Adversarial Learning". WWW 2020. [*paper*](https://dl.acm.org/doi/10.1145/3366423.3380155)
- (wRAN) Ningyu Zhang, Shumin Deng, Zhanlin Sun, Jiaoyan Chen, Wei Zhang, Huajun Chen. "Relation Adversarial Network for Low Resource Knowledge Graph Completion". WWW 2020. [*paper*](https://dl.acm.org/doi/10.1145/3366423.3380089)

## 2021

### Journal

#### IEEE Internet of Things Journal

- (TECRL) Feng Zhao, Tao Xu, Langjunqing Jin, Hai Jin. "Convolutional Network Embedding of Text-Enhanced Representation for Knowledge Graph Completion". IEEE Internet of Things Journal 2021. [*paper*](https://ieeexplore.ieee.org/document/9266078)

#### Neural Networks

- (DAPath) Prayag Tiwari, Hongyin Zhu, Hari Mohan Pandey. "DAPath: Distance-aware knowledge graph reasoning based on deep reinforcement learning". Neural Networks 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S089360802030410X?via%3Dihub)

- (HiAM) Ting Ma, Shangwen Lv, Longtao Huang, Songlin Hu. "HiAM: A Hierarchical Attention based Model for knowledge graph multi-hop reasoning". Neural Networks 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0893608021002409?via%3Dihub)
- (LSUs) Zhao Zhang, Fuzhen Zhuang, Meng Qu, Zheng-Yu Niu, Hui Xiong, Qing He. "Knowledge graph embedding with shared latent semantic units". Neural Networks 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0893608021000551?via%3Dihub)

#### Information Sciences

- (Rule-IC) Qika Lin, Jun Liu, Yudai Pan, Lingling Zhang, Xin Hu, Jie Ma. "Ruleenhanced iterative complementation for knowledge graph reasoning". Information Sciences 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0020025521006319?via%3Dihub)

#### IEEE Transactions on Knowledge and Data Engineering

- (KSR) Han Xiao, Yidong Chen, Xiaodong Shi. "Knowledge Graph Embedding Based on Multi-View Clustering Framework". IEEE Transactions on Knowledge and Data Engineering 2021. [*paper*](https://ieeexplore.ieee.org/document/8778709)
- (RLvLR) Pouya Ghiasnezhad Omran, Kewen Wang, Zhe Wang. "An EmbeddingBased Approach to Rule Learning in Knowledge Graphs". IEEE Transactions on Knowledge and Data Engineering 2021. [*paper*](https://ieeexplore.ieee.org/document/8839576)
- (TAPR) Ying Shen, Ning Ding, Hai-Tao Zheng, Yaliang Li, Min Yang. "Modeling Relation Paths for Knowledge Graph Completion". IEEE Transactions on Knowledge and Data Engineering 2021. [*paper*](https://ieeexplore.ieee.org/document/8974254)

#### Expert Systems with Applications

- (KGEL) Adnan Zeb, Anwar Ul Haq, Defu Zhang, Junde Chen, Zhiguo Gong. "KGEL: A novel end-to-end embedding learning framework for knowledge graph completion". Expert Systems with Applications 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0957417420309039?via%3Dihub)

- (PRN) Wan-Kon Lee, Won-Chul Shin, Batselem Jagvaral, Jae-Seung Roh, Min-Sung Kim, Min-Ho Lee, Hyun-Kyu Park, Young-Tack Park. "A path-based relation networks model for knowledge graph completion". Expert Systems with Applications 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0957417421007041?via%3Dihub)

#### Applied Soft Computing

- (TPath) Luyi Bai, Wenting Yu, Mingzhuo Chen, Xiangnan Ma. "Multi-hop reasoning over paths in temporal knowledge graphs using reinforcement learning". Applied Soft Computing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S1568494621000673?via%3Dihub)

#### Knowledge Based Systems

- (CoRelatE) Yan Huang, Haili Sun, Ke Xu, Songfeng Lu, Tongyang Wang, Xinfang Zhang. "CoRelatE: Learning the correlation in multi-fold relations for knowledge graph embedding". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705120307309?via%3Dihub)

- (CounterFactual) Zikang Wang, Linjing Li, Daniel Zeng, Xiaofei Wu. "Incorporating prior knowledge from counterfactuals into knowledge graph reasoning". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121002987?via%3Dihub)
- (KMAE) Dan Jiang, Ronggui Wang, Juan Yang, Lixia Xue. "Kernel multi-attention neural network for knowledge graph embedding". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121004500?via%3Dihub)
- (MGTransR) Jianxing Zheng, Qinwen Li, Jian Liao, Suge Wang. "Explainable link prediction based on multi-granularity relation-embedded representation". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S095070512100664X?via%3Dihub) 
- (MöbiusE) Yao Chen, Jiangang Liu, Zhe Zhang, Shiping Wen, Wenjun Xiong. "MöbiusE: Knowledge Graph Embedding on Möbius Ring". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121004445?via%3Dihub)
- (MRotatE) Xuqian Huang, Jiuyang Tang, Zhen Tan, Weixin Zeng, Ji Wang, Xiang Zhao. "Knowledge graph embedding by relational and entity rotation". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/pii/S0950705121005724?via%3Dihub) [*code*](https://github.com/XuqianHuang/MRotatE)
- (RHGNN) Adnan Zeb, Anwar Ul Haq, Junde Chen, Zhenfeng Lei, Defu Zhang. "Learning hyperbolic attention-based embeddings for link prediction in knowledge graphs". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121006316?via%3Dihub)
- (TAGAT) Yuzhuo Wang, Hongzhi Wang, Junwei He, Wenbo Lu, Shuolin Gao. "TAGAT: Type-Aware Graph Attention networks for reasoning over knowledge graphs". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121007620?via%3Dihub)
- (TimE) Qianjin Zhang, Ronggui Wang, Juan Yang, Lixia Xue. "Knowledge graph embedding by translating in time domain space for link prediction". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705120306936?via%3Dihub)
- (Top-k-Query) Yuxiang Wang, Xiaoliang Xu, Qifan Hong, Jiahui Jin, Tianxing Wu. "Top-k star queries on knowledge graphs through semantic-aware bounding match scores". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S095070512030784X?via%3Dihub)
- (TrustE) Yu Zhao, Zhiquan Li, Wei Deng, Ruobing Xie, Qing Li. "Learning entity type structured embeddings with trustworthiness on noisy knowledge graphs". Knowledge Based Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705120307590?via%3Dihub)

#### Future Generation Computer Systems

- (Hash) Meng Wang, Weitong Chen, Sen Wang, Yinlin Jiang, Lina Yao, Guilin Qi. "Efficient search over incomplete knowledge graphs in binarized embedding space". Future Generation Computer Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0167739X21001217?via%3Dihub)
- (SBIGMat) Ali Assi, Wajdi Dhifli. "Instance Matching in Knowledge Graphs through random walks and semantics". Future Generation Computer Systems 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0167739X21001369?via%3Dihub)

#### Engineering Applications of Artificial Intelligence

- (CAFE) Agustín Borrego, Daniel Ayala, Inma Hernández, Carlos R. Rivero, David Ruiz. "CAFE: Knowledge graph completion using neighborhood-aware features". Engineering Applications of Artificial Intelligence 2021". [*paper*](https://www.sciencedirect.com/science/article/pii/S0952197621001500?via%3Dihub) [*code*](https://github.com/DEAL-US/CAFE)

#### Neurocomputing

- (Deep-IDA) Qi Wang, Yongsheng Hao, Feng Chen. "Deepening the IDA algorithm for knowledge graph reasoning through neural network architecture". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231220319408?via%3Dihub)
- (DSKRL) Tianyang Shao, Xinyi Li, Xiang Zhao, Hao Xu, Weidong Xiao. "DSKRL: A dissimilarity-support-aware knowledge representation learning framework on noisy knowledge graph". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221009590?via%3Dihub)
- (GAKGE) Chen Li, Xutan Peng, Yuhang Niu, Shanghang Zhang, Hao Peng, Chuan Zhou, Jianxin Li. "Learning graph attention-aware knowledge graph embedding". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221010961?via%3Dihub)
- (HA-RotatE) Shensi Wang, Kun Fu, Xian Sun, Zequn Zhang, Shuchao Li, Li Jin. "Hierarchical-aware relation rotational knowledge graph embedding for link prediction". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221008560?via%3Dihub)
- (IE-RCN) Zhifei Li, Hai Liu, Zhaoli Zhang, Tingting Liu, Jiangbo Shu. "Recalibration convolutional networks for learning interaction knowledge graph embedding". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231220318506?via%3Dihub) [*code*](https://github.com/zhifei1993/RCN)
- (KRC) Mingda Li, Zhengya Sun, Siheng Zhang, Wensheng Zhang. "Enhancing knowledge graph embedding with relational constraints". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231220318932?via%3Dihub)
- (MemoryPath) Shuangyin Li, Heng Wang, Rong Pan, Mingzhi Mao. "MemoryPath: A deep reinforcement learning framework for incorporating memory component into knowledge graph reasoning". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231220312959?via%3Dihub)
- (MTE) Yingying Xue, Jiahui Jin, Aibo Song, Yingxue Zhang, Yangyang Liu, Kaixuan Wang. "Relation-based multi-type aware knowledge graph embedding". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S092523122100758X?via%3Dihub)
- (SRGCN) Zikang Wang, Linjing Li, Daniel Zeng. "SRGCN: Graph-based multi-hop reasoning on knowledge graphs". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221007530?via%3Dihub)
- (Trans4E) Mojtaba Nayyeri, Gökce Müge Cil, Sahar Vahdati, Francesco Osborne, Mahfuzur Rahman, Simone Angioni, Angelo A. Salatino, Diego Reforgiato Recupero, Nadezhda Vassilyeva, Enrico Motta, Jens Lehmann. "Trans4E: Link prediction on scholarly knowledge graphs". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221009607?via%3Dihub)
- (TRAR) Xiaojuan Zhao, Yan Jia, Aiping Li, Rong Jiang, Kai Chen, Ye Wang. "Target relational attention-oriented knowledge graph reasoning". Neurocomputing 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221009668?via%3Dihub)

#### Journal of Machine Learning Research

- (PyKEEN) Mehdi Ali, Max Berrendorf, Charles Tapley Hoyt, Laurent Vermue, Sahand Sharifzadeh, Volker Tresp, Jens Lehmann. "PyKEEN 1.0: A Python Library for Training and Evaluating Knowledge Graph Embeddings". Journal of Machine Learning Research 2021. [*paper*](https://jmlr.org/papers/v22/20-825.html) [*code*](https://github.com/pykeen/pykeen)
- (Pykg2vec) Shih-Yuan Yu, Sujit Rokka Chhetri, Arquimedes Canedo, Palash Goyal, Mohammad Abdullah Al Faruque. "Pykg2vec: A Python Library for Knowledge Graph Embedding". Journal of Machine Learning Research 2021. [*paper*](https://jmlr.org/papers/v22/19-433.html) [*code*](https://github.com/Sujit-O/pykg2vec)

#### Neural Computing and Applications

- (BDR+CA) Kairong Hu, Hai Liu, Choujun Zhan, Yong Tang, Tianyong Hao. "Learning knowledge graph embedding with a bi-directional relation encoding network and a convolutional autoencoder decoding network". Neural Computing and Applications 2021. [*paper*](https://link.springer.com/article/10.1007%2Fs00521-020-05654-4)
- (DMACM) Jin Huang, Tinghua Zhang, Jia Zhu, Weihao Yu, Yong Tang, Yang He. "A deep embedding model for knowledge graph completion based on attention mechanism". Neural Computing and Applications 2021. [*paper*](https://link.springer.com/article/10.1007%2Fs00521-021-05742-z)
- (NKSGAN) Hai Liu, Kairong Hu, Fu Lee Wang, Tianyong Hao. "Correction to: Aggregating neighborhood information for negative sampling for knowledge graph embedding". Neural Computing and Applications 2021. [*paper*](https://link.springer.com/article/10.1007%2Fs00521-020-04940-5)
- (SD-GAT) Xue Zhou, Bei Hui, Lizong Zhang, Kexi Ji. "A structure distinguishable graph attention network for knowledge base completion". Neural Computing and Applications 2021. [*paper*](https://link.springer.com/article/10.1007%2Fs00521-021-06221-1)
- (W-KG2Vec) Phuc Do, Phu Pham. "W-KG2Vec: a weighted text-enhanced metapath-based knowledge graph embedding for similarity search". Neural Computing and Applications 2021. [*paper*](https://link.springer.com/article/10.1007/s00521-021-06252-8)

#### Ad Hoc Networks

- (TRFR) Yao Zhang, Hengpeng Xu, Xu Zhang, Xingxing Wu, Zhenglu Yang. "TRFR: A ternary relation link prediction framework on Knowledge graphs". Ad Hoc Networks 2021. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S1570870520307319?via%3Dihub)

#### International Journal of Machine Learning and Cybernetics

- (Caps-OWKG) Yuhan Wang, Weidong Xiao, Zhen Tan, Xiang Zhao. "Caps-OWKG: a capsule network model for open-world knowledge graph". International Journal of Machine Learning and Cybernetics 2021. [*paper*](https://link.springer.com/article/10.1007%2Fs13042-020-01259-4)

### Conference

#### ICLR

- (PMI) Carl Allen, Ivana Balazevic, Timothy Hospedales. "Interpreting Knowledge Graph Relation Representation from Word Embeddings". ICLR 2021. [*paper*](https://iclr.cc/virtual/2021/poster/2656)
- (RNNLogic) Meng Qu, Junkun Chen, Louis-Pascal A Xhonneux, Yoshua Bengio, Jian Tang. "RNNLogic: Learning Logic Rules for Reasoning on Knowledge Graphs". ICLR 2021. [*paper*](https://iclr.cc/virtual/2021/poster/3084) [*code*](https://github.com/DeepGraphLearning/RNNLogic)
- (xERTE) Zhen Han, Peng Chen, Yunpu Ma, Volker Tresp. "Explainable Subgraph Reasoning for Forecasting on Temporal Knowledge Graphs". ICLR 2021. [*paper*](https://iclr.cc/virtual/2021/poster/3378) [*code*](https://github.com/TemporalKGTeam/xERTE)

#### AAAI

- (5E) Mojtaba Nayyeri, Sahar Vahdati, Can Aykul, Jens Lehmann. "5 Knowledge Graph Embeddings with Projective Transformations". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/17095)
- (BiQE) Bhushan Kotnis, Carolin Lawrence, Mathias Niepert. "Answering Complex Queries in Knowledge Graphs with Bidirectional Sequence Encoders". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16630)
- (ChronoR) Ali Sadeghian, Mohammadreza Armandpour, Anthony Colas, Daisy Zhe Wang. "ChronoR: Rotation Based Temporal Knowledge Graph Embedding". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16802)
- (CLKGE) Mehrnoosh Mirtaheri. "Relational Learning to Capture the Dynamics and Sparsity of Knowledge Graphs". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/17859)
- (CyGNet) Cunchao Zhu, Muhao Chen, Changjun Fan, Guangquan Cheng, Yan Zhang. "Learning from History: Modeling Temporal Knowledge Graphs with Sequential Copy-Generation Networks". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16604) [*code*](https://github.com/CunchaoZ/CyGNet)
- (DualE) Zongsheng Cao, Qianqian Xu, Zhiyong Yang, Xiaochun Cao, Qingming Huang. "Dual Quaternion Knowledge Graph Embeddings". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16850) [*code*](https://github.com/Lion-ZS/DualE)
- (GaussianPath) Guojia Wan, Bo Du. "GaussianPath: A Bayesian Multi-Hop Reasoning Framework for Knowledge Graph Reasoning". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16565)
- (NLSM) Tony Gracious, Shubham Gupta, Arun Kanthali, Rui M. Castro, Ambedkar Dukkipati. "Neural Latent Space Model for Dynamic Networks and Temporal Knowledge Graphs". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16526)
- (PASSLEAF) Zhu-Mu Chen, Mi-Yen Yeh, Tei-Wei Kuo. "PASSLEAF: A Pool-based Semi-Supervised LEArning Framework for Uncertain Knowledge Graph Embedding". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16522)
- (TACT) Jiajun Chen, Huarui He, Feng Wu, Jie Wang. "Topology-Aware Correlations Between Relations for Inductive Link Prediction in Knowledge Graphs". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16779) [*code*](https://github.com/MIRALab-USTC/KG-TACT)
- (TaRP) Zijun Cui, Pavan Kapanipathi, Kartik Talamadupula, Tian Gao, Qiang Ji. "Typeaugmented Relation Prediction in Knowledge Graphs". AAAI 2021. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/16879)

#### NeurIPS

- (ConE) Zhanqiu Zhang, Jie Wang, Jiajun Chen, Shuiwang Ji, Feng Wu. "ConE: Cone Embeddings for Multi-Hop Reasoning over Knowledge Graphs". NeurIPS 2021. [*paper*](https://proceedings.neurips.cc/paper/2021/hash/a0160709701140704575d499c997b6ca-Abstract.html) [*code*](https://github.com/MIRALab-USTC/QE-ConE)

#### ACL

- (CluSTeR) Zixuan Li, Xiaolong Jin, Saiping Guan, Wei Li, Jiafeng Guo, Yuanzhuo Wang, Xueqi Cheng. "Search from History and Reason for Future: Two-stage Reasoning on Temporal Knowledge Graphs". ACL/IJCNLP 2021. [*paper*](https://aclanthology.org/2021.acl-long.365/)
- (EIGAT) Yu Zhao, Han Zhou, Ruobing Xie, Fuzhen Zhuang, Qing Li, Ji Liu. "Incorporating Global Information in Local Attention for Knowledge Representation Learning". ACL/IJCNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-acl.115/) [*code*](https://github.com/zhouhanhanhan/EIGAT)
- (GRAN) Quan Wang, Haifeng Wang, Yajuan Lyu, Yong Zhu. "Link Prediction on Nary Relational Facts: A Graph-based Approach". ACL/IJCNLP (Findings) 2021.[*paper*](https://aclanthology.org/2021.findings-acl.35/)
- (HERCULES) Sebastien Montella, Lina Maria Rojas-Barahona, Johannes Heinecke."Hyperbolic Temporal Knowledge Graph Embeddings with Relational and Time Curvatures". ACL/IJCNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-acl.292/)
- (InferenceAttack) Peru Bhardwaj, John D. Kelleher, Luca Costabello, Declan O'Sullivan. "Poisoning Knowledge Graph Embeddings via Relation Inference Patterns". ACL/IJCNLP 2021. [*paper*](https://aclanthology.org/2021.acl-long.147/) [*code*](https://github.com/PeruBhardwaj/InferenceAttack)
- (InferWiki) Yixin Cao, Xiang Ji, Xin Lv, Juanzi Li, Yonggang Wen, Hanwang Zhang. "Are Missing Links Predictable? An Inferential Benchmark for Knowledge Graph Completion". ACL/IJCNLP 2021. [*paper*](https://aclanthology.org/2021.acl-long.534/) [*code*](https://github.com/TaoMiner/inferwiki)
- (MLMLM) Louis Clouâtre, Philippe Trempe, Amal Zouaq, Sarath Chandar. "MLMLM: Link Prediction with Mean Likelihood Masked Language Model". ACL/IJCNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-acl.378/) [*code*](https://github.com/763337092/MLMLM)
- (OKGIT) Chandrahas, Partha P. Talukdar. "OKGIT: Open Knowledge Graph Link Prediction with Implicit Types". ACL/IJCNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-acl.225/) [*code*](https://github.com/Chandrahasd/OKGIT)
- (PairRE) Linlin Chao, Jianshan He, Taifeng Wang, Wei Chu. "PairRE: Knowledge Graph Embeddings via Paired Relation Vectors". ACL/IJCNLP 2021. [*paper*](https://aclanthology.org/2021.acl-long.336/) [*code*](https://github.com/alipay/KnowledgeGraphEmbeddingsViaPairedRelationVectors_PairRE)
- (RARL) Zhongni Hou, Xiaolong Jin, Zixuan Li, Long Bai. "Rule-Aware Reinforcement Learning for Knowledge Graph Reasoning". ACL/IJCNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-acl.412/)
- (SCE) Hidetaka Kamigaito, Katsuhiko Hayashi. "Unified Interpretation of Softmax Cross-Entropy and Negative Sampling: With Case Study for Knowledge Graph Embedding". ACL/IJCNLP 2021. [*paper*](https://aclanthology.org/2021.acl-long.429/)

#### IJCAI

- (FocusE) Sumit Pai, Luca Costabello. "Learning Embeddings from Knowledge Graphs With Numeric Edge Attributes". IJCAI 2021. [*paper*](https://www.ijcai.org/proceedings/2021/395)
- (HIPNet) Yongquan He, Peng Zhang, Luchen Liu, Qi Liang, Wenyuan Zhang, Chuang Zhang, "HIP Network: Historical Information Passing Network for Extrapolation Reasoning on Temporal Knowledge Graph". IJCAI 2021. [*paper*](https://www.ijcai.org/proceedings/2021/264) [*code*](https://github.com/Yongquan-He/HIP-network)
- (NIC) Kai Wang, Yu Liu, Quan Z. Sheng. "Neighborhood Intervention Consistency: Measuring Confidence for Knowledge Graph Link Prediction". IJCAI 2021. [*paper*](https://www.ijcai.org/proceedings/2021/288)

#### EMNLP

- (BiQUE) Jia Guo, Stanley Kok. "BiQUE: Biquaternionic Embeddings of Knowledge Graphs". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.657/) [*code*](https://github.com/guojiapub/BiQUE)
- (C3) Bo Ouyang, Wenbing Huang, Runfa Chen, Zhixing Tan, Yang Liu, Maosong Sun, Jihong Zhu. "Knowledge Representation Learning with Contrastive Completion Coding". EMNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-emnlp.263/)
- (CET) Weiran Pan, Wei Wei, Xian-Ling Mao. "Context-aware Entity Typing in Knowledge Graphs". EMNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-emnlp.193/) [*code*](https://github.com/CCIIPLab/CET)
- (DataCollection) Kenneth Church, Yuchen Bian. "Data Collection vs. Knowledge Graph Completion: What is Needed to Improve Coverage?". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.501/)
- (EventKE) Zixuan Zhang, Hongwei Wang, Han Zhao, Hanghang Tong, Heng Ji. "EventKE: Event-Enhanced Knowledge Graph Embedding". EMNLP (Findings) 2021\. [*paper*](https://aclanthology.org/2021.findings-emnlp.120/)
- (FieldE) Mojtaba Nayyeri, Chengjin Xu, Franca Hoffmann, Mirza Mohtashim Alam, Jens Lehmann, Sahar Vahdati. "Knowledge Graph Representation Learning using Ordinary Differential Equations". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.750/)
- (HBE) Zhe Pan, Peng Wang. "Hyperbolic Hierarchy-Aware Knowledge Graph Embedding for Link Prediction". EMNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-emnlp.251/)
- (HittER) Sanxing Chen, Xiaodong Liu, Jianfeng Gao, Jian Jiao, Ruofei Zhang, Yangfeng Ji. "HittER: Hierarchical Transformers for Knowledge Graph Embeddings". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.812/) [*code*](https://github.com/sanxing-chen/HittER)
- (KGBiasDetec) Daphna Keidar, Mian Zhong, Ce Zhang, Yash Raj Shrestha, Bibek Paudel. "Towards Automatic Bias Detection in Knowledge Graphs". EMNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-emnlp.321/)
- (KGE+AT) Jinfa Yang, Yongjie Shi, Xin Tong, Robin Wang, Taiyan Chen, Xianghua Ying. "Improving Knowledge Graph Embedding Using Affine Transformations of Entities Corresponding to Each Relation". EMNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-emnlp.46/)
- (P-INT) Jingwen Xu, Jing Zhang, Xirui Ke, Yuxiao Dong, Hong Chen, Cuiping Li, Yongbin Liu. "P-INT: A Path-based Interaction Model for Few-shot Knowledge Graph Completion". EMNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-emnlp.35/)
- (Pre-Training) Vid Kocijan, Thomas Lukasiewicz. "Knowledge Base Completion Meets Transfer Learning". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.524/) [*code*](https://github.com/vid-koci/KBCtransferlearning)
- (RelDiff) Hitarth Narvala, Graham McDonald, Iadh Ounis. "RelDiff: Enriching Knowledge Graph Relation Representations for Sensitivity Classification". EMNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-emnlp.311/)
- (RotL) Kai Wang, Yu Liu, Dan Lin, Michael Sheng. "Hyperbolic Geometry is Not Necessary: Lightweight Euclidean-Based Models for Low-Dimensional Knowledge Graph Embeddings". EMNLP (Findings) 2021. [*paper*](https://aclanthology.org/2021.findings-emnlp.42/)
- (SFBR) Zongwei Liang, Junan Yang, Hui Liu, Ke-Ju Huang. "A Semantic Filter Based on Relations for Knowledge Graph Completion". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.625/)
- (TANGO) Zhen Han, Zifeng Ding, Yunpu Ma, Yujia Gu, Volker Tresp. "Learning Neural Ordinary Equations for Forecasting Future Links on Temporal Knowledge Graphs". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.658/)
- (TEA-GNN) Chengjin Xu, Fenglong Su, Jens Lehmann. "Time-aware Graph Neural Network for Entity Alignment between Temporal Knowledge Graphs". EMNLP 2021\. [*paper*](https://aclanthology.org/2021.emnlp-main.709/) [*code*](https://github.com/soledad921/TEA-GNN)
- (TEE) Zhen Han, Gengyuan Zhang, Yunpu Ma, Volker Tresp. "Time-dependent Entity Embedding is not All You Need: A Re-evaluation of Temporal Knowledge Graph Completion Models under a Unified Framework". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.639/)
- (TITer) Haohai Sun, Jialun Zhong, Yunpu Ma, Zhen Han, Kun He. "TimeTraveler: Reinforcement Learning for Temporal Knowledge Graph Forecasting". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.655/) [*code*](https://github.com/JHL-HUST/TITer)
- (UniKER) Kewei Cheng, Ziqing Yang, Ming Zhang, Yizhou Sun. "UniKER: A Unified Framework for Combining Embedding and Definite Horn Rule Reasoning for Knowledge Graph Inference". EMNLP 2021. [*paper*](https://aclanthology.org/2021.emnlp-main.769/) [*code*](https://github.com/vivian1993/UniKER)

#### NAACL

- (BEUrRE) Xuelu Chen, Michael Boratko, Muhao Chen, Shib Sankar Dasgupta, Xiang Lorraine Li, Andrew McCallum. "Probabilistic Box Embeddings for Uncertain Knowledge Graph Reasoning". NAACL-HLT 2021. [*paper*](https://www.aclweb.org/anthology/2021.naacl-main.68/) [*code*](https://github.com/stasl0217/beurre)
- (EDGE) Saed Rezayi, Handong Zhao, Sungchul Kim, Ryan A. Rossi, Nedim Lipka, Sheng Li. "Edge: Enriching Knowledge Graph Embeddings with External Text". NAACL-HLT 2021. [*paper*](https://www.aclweb.org/anthology/2021.naacl-main.221/)
- (KRE) Shuai Zhang, Xi Rao, Yi Tay, Ce Zhang. "Knowledge Router: Learning Disentangled Representations for Knowledge Graphs". NAACL-HLT 2021. [*paper*](https://www.aclweb.org/anthology/2021.naacl-main.1/)
- (ProcrustEs) Xutan Peng, Guanyi Chen, Chenghua Lin, Mark Stevenson. "Highly Efficient Knowledge Graph Embedding Learning with Orthogonal Procrustes Analysis". NAACL-HLT 2021. [*paper*](https://www.aclweb.org/anthology/2021.naacl-main.187/) [*code*](https://github.com/Pzoom522/ProcrustEs-KGE)
- (RTFE) Youri Xu, Haihong E, Meina Song, Wenyu Song, Xiaodong Lv, Haotian Wang, Jinrui Yang. "RTFE: A Recursive Temporal Fact Embedding Framework for Temporal Knowledge Graph Completion". NAACL-HLT 2021. [*paper*](https://www.aclweb.org/anthology/2021.naacl-main.451/)
- (TeLM) Chengjin Xu, Yung-Yu Chen, Mojtaba Nayyeri, Jens Lehmann. "Temporal Knowledge Graph Completion using a Linear Temporal Regularizer and Multivector Embeddings". NAACL-HLT 2021. [*paper*](https://www.aclweb.org/anthology/2021.naacl-main.202/) [*code*](https://github.com/soledad921/TeLM)

#### KDD

- (KompaRe) Lihui Liu, Boxin Du, Yi Ren Fung, Heng Ji, Jiejun Xu, Hanghang Tong. "KompaRe: A Knowledge Graph Comparative Reasoning System". KDD 2021. [*paper*](https://dl.acm.org/doi/10.1145/3447548.3467128)
- (NewLook) Lihui Liu, Boxin Du, Heng Ji, ChengXiang Zhai, Hanghang Tong. "Neural-Answering Logical Queries on Knowledge Graphs". KDD 2021. [*paper*](https://dl.acm.org/doi/10.1145/3447548.3467375)
- (PathCon) Hongwei Wang, Hongyu Ren, Jure Leskovec. "Relational Message Passing for Knowledge Graph Completion". KDD 2021. [*paper*](https://dl.acm.org/doi/10.1145/3447548.3467247)
- (RGTN) Han Huang, Leilei Sun, Bowen Du, Chuanren Liu, Weifeng Lv, Hui Xiong. "Representation Learning on Knowledge Graphs for Node Importance Estimation". KDD 2021. [*paper*](https://dl.acm.org/doi/10.1145/3447548.3467342) [*code*](https://github.com/GRAPH-0/RGTN-NIE)
- (T-GAP) Jaehun Jung, Jinhong Jung, U. Kang. "Learning to Walk across Time for Interpretable Temporal Knowledge Graph Completion". KDD 2021. [*paper*](https://dl.acm.org/doi/10.1145/3447548.3467292) [*code*](https://github.com/anonymoususer99/T-GAP)

#### SIGIR

- (GANA) Guanglin Niu, Yang Li, Chengguang Tang, Ruiying Geng, Jian Dai, Qiao Liu, Hao Wang, Jian Sun, Fei Huang, Luo Si. "Relational Learning with Gated and Attentive Neighbor Aggregator for Few-Shot Knowledge Graph Completion". SIGIR 2021. [*paper*](https://dl.acm.org/doi/10.1145/3404835.3462925) [*code*](https://github.com/ngl567/GANA-FewShotKGC)
- (META-KGE) Chanyoung Chung, Joyce Jiyoung Whang. "Knowledge Graph Embedding via Metagraph Learning". SIGIR 2021. [*paper*](https://dl.acm.org/doi/10.1145/3404835.3463072) [*code*](https://github.com/bdi-lab/meta_kge)
- (MetaP) Zhiyi Jiang, Jianliang Gao, Xinqi Lv. "MetaP: Meta Pattern Learning for OneShot Knowledge Graph Completion". SIGIR 2021. [*paper*](https://dl.acm.org/doi/10.1145/3404835.3463086) [*code*](https://github.com/jzystc/MetaP)
- (RE-GCN) Zixuan Li, Xiaolong Jin, Wei Li, Saiping Guan, Jiafeng Guo, Huawei Shen, Yuanzhuo Wang, Xueqi Cheng. "Temporal Knowledge Graph Reasoning Based on Evolutional Representation Learning". SIGIR 2021. [*paper*](https://dl.acm.org/doi/10.1145/3404835.3462963) [*code*](https://github.com/Lee-zix/RE-GCN) 
- (TIE) Jiapeng Wu, Yishi Xu, Yingxue Zhang, Chen Ma, Mark Coates, Jackie Chi Kit Cheung. "TIE: A Framework for Embedding-based Incremental Temporal Knowledge Graph Completion". SIGIR 2021. [*paper*](https://dl.acm.org/doi/10.1145/3404835.3462961) [*code*](https://github.com/JiapengWu/Time-Aware-Incremental-Embedding)

#### ICDE

- (ERAS) Shimin Di, Quanming Yao, Yongqi Zhang, Lei Chen. "Efficient Relation-aware Scoring Function Search for Knowledge Graph Embedding". ICDE 2021. [*paper*](https://ieeexplore.ieee.org/document/9458750) [*code*](https://github.com/AutoML-Research/ERAS)

#### CIKM

- (CyclE) Han Yang, Leilei Zhang, Bingning Wang, Ting Yao, Junfei Liu. "Cycle or Minkowski: Which is More Appropriate for Knowledge Graph Embedding". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482245)
- (DisenKGAT) Junkang Wu, Wentao Shi, Xuezhi Cao, Jiawei Chen, Wenqiang Lei, Fuzheng Zhang, Wei Wu, Xiangnan He. "DisenKGAT: Knowledge Graph Embedding with Disentangled Graph Attention Network". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482424) [*code*](https://github.com/junkangwu/DisenKGAT)
- (DT-GCN) Yuxin Shen, Zhao Li, Xin Wang, Jianxin Li, Xiaowang Zhang. "DataType-Aware Knowledge Graph Representation Learning in Hyperbolic Space". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482421)
- (FKGE) Hao Peng, Haoran Li, Yangqiu Song, Vincent W. Zheng, Jianxin Li. "Differentially Private Federated Knowledge Graphs Embedding". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482252) [*code*](https://github.com/HKUST-KnowComp/FKGE)
- (GrpKG) Han Yang, Junfei Liu. "Knowledge Graph Representation Learning as Groupoid: Unifying TransE, RotatE, QuatE, ComplEx". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482442)
- (HopfE) Anson Bastos, Kuldeep Singh, Abhishek Nadgeri, Saeedeh Shekarpour, Isaiah Onando Mulang, Johannes Hoffart. "HopfE: Knowledge Graph Representation Learning using Inverse Hopf Fibrations". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482263) [*code*](https://github.com/ansonb/HopfE)
- (HRFN) Yufeng Zhang, Weiqing Wang, Wei Chen, Jiajie Xu, An Liu, Lei Zhao. "Meta-Learning Based Hyper-Relation Feature Modeling for Out-of-Knowledge-Base Embedding". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482367)
- (LightKG) Haoyu Wang, Yaqing Wang, Defu Lian, Jing Gao. "A Lightweight Knowledge Graph Embedding Framework for Efficient Inference and Storage". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482224)
- (REFORM) Song Wang, Xiao Huang, Chen Chen, Liang Wu, Jundong Li. "REFORM: Error-Aware Few-Shot Knowledge Graph Completion". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482470)
- (THML) Shangfei Zheng, Wei Chen, Pengpeng Zhao, An Liu, Junhua Fang, Lei Zhao. "When Hardness Makes a Difference: Multi-Hop Knowledge Graph Reasoning over Few-Shot Relations". CIKM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3459637.3482402)

#### WSDM

- (DBKGE) Siyuan Liao, Shangsong Liang, Zaiqiao Meng, Qiang Zhang. "Learning Dynamic Embeddings for Temporal Knowledge Graphs". WSDM 2021. [*paper*](https://dl.acm.org/doi/10.1145/3437963.3441741)

#### DASFAA

- (GMUC) Jiatao Zhang, Tianxing Wu, Guilin Qi. "Gaussian Metric Learning for FewShot Uncertain Knowledge Graph Completion". DASFAA 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-73194-6_18)

- (SEwA) Zhijuan Du. "Sequence Embedding for Zero or Low Resource Knowledge Graph Completion". DASFAA 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-73194-6_20)
- (ST-ConvKB) Jiasheng Zhang, Shuang Liang, Zhiyi Deng, Jie Shao. "Spatial- Temporal Attention Network for Temporal Knowledge Graph Completion". DASFAA 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-73194-6_15)
- (TransMTL) Jiaheng Dou, Bing Tian, Yong Zhang, Chunxiao Xing. "A Novel Embedding Model for Knowledge Graph Completion Based on Multi-Task Learning". DASFAA 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-73194-6_17) [*code*](https://github.com/thu-west/MTL-gat)

#### ECML-PKDD

- (PaGNN) Shuo Yang, Binbin Hu, Zhiqiang Zhang, Wang Sun, Yang Wang, Jun Zhou, Hongyu Shan, Yuetian Cao, Borui Ye, Yanming Fang, Quan Yu. "Inductive Link Prediction with Interactive Structure Learning on Attributed Graph". ECML/PKDD 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-86520-7_24)
- (WD/MMD) Luu Huu Phuc, Koh Takeuchi, Seiji Okajima, Arseny Tolmachev, Tomoyoshi Takebayashi, Koji Maruhashi, Hisashi Kashima. "Inter-domain Multi-relational Link Prediction". ECML/PKDD 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-86520-7_18) [*code*](https://github.com/phucdoitoan/inter-domain_lp)

#### ESWC

- (ConEx) Caglar Demir, Axel-Cyrille Ngonga Ngomo. "Convolutional Complex Knowledge Graph Embeddings". ESWC 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-77385-4_24) [*code*](https://github.com/dice-group/Convolutional-Complex-Knowledge-Graph-Embeddings) [*code*](https://github.com/Jean-KOUAGOU/ConEx)
- (RETRA) Simon Werner, Achim Rettinger, Lavdim Halilaj, Jürgen Lüttin. "RETRA: Recurrent Transformers for Learning Temporally Contextualized Knowledge Graph Embeddings". ESWC 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-77385-4_25) [*code*](https://github.com/siwer/Retra)
- (Semantic) Nitisha Jain, Jan-Christoph Kalo, Wolf-Tilo Balke, Ralf Krestel. "Do Embeddings Actually Capture Knowledge Graph Semantics?". ESWC 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-77385-4_9) [*code*](https://github.com/nitishajain/KGESemanticAnalysis)
- (TransROWL) Claudia d'Amato, Nicola Flavio Quatraro, Nicola Fanizzi. "Injecting Background Knowledge into Embedding Models for Predictive Tasks on Knowledge Graphs". ESWC 2021. [*paper*](https://link.springer.com/chapter/10.1007%2F978-3-030-77385-4_26)

#### WWW

- (AMIE) Sudhanshu Tiwari, Iti Bansal, Carlos R. Rivero. "Revisiting the Evaluation Protocol of Knowledge Graph Completion Methods for Link Prediction". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3449856)
- (ATransN) Huijuan Wang, Shuangyin Li, Rong Pan. "An Adversarial Transfer Network for Knowledge Representation Learning". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3450064) [*code*](https://github.com/LemonNoel/ATransN)
- (KE-GCN) Donghan Yu, Yiming Yang, Ruohong Zhang, Yuexin Wu. "Knowledge Embedding Based Graph Convolutional Network". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3449925) [*code*](https://github.com/Lee-zix/RE-GCN)
- (M2GNN) Shen Wang, Xiaokai Wei, Cicero Nogueira dos Santos, Zhiguo Wang, Ramesh Nallapati, Andrew O. Arnold, Bing Xiang, Philip S. Yu, Isabel F. Cruz. "Mixed-Curvature Multi-Relational Graph Neural Network for Knowledge Graph Completion". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3450118)
- (MQuadE) Jinxing Yu, Yunfeng Cai, Mingming Sun, Ping Li. "MQuadE: a Unified Model for Knowledge Fact Embedding". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3449879)
- (MulDE) Kai Wang, Yu Liu, Qian Ma, Quan Z. Sheng. "MulDE: Multi-teacher Knowledge Distillation for Low-dimensional Knowledge Graph Embeddings". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3449898)
- (NS-KGE) Zelong Li, Jianchao Ji, Zuohui Fu, Yingqiang Ge, Shuyuan Xu, Chong Chen, Yongfeng Zhang. "Efficient Non-Sampling Knowledge Graph Embedding". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3449859) [*code*](https://github.com/rutgerswiselab/NS-KGE)
- (RAW) Yu Liu, Quanming Yao, Yong Li. "Role-Aware Modeling for N-ary Relational Knowledge Bases". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3449874) [*code*](https://github.com/liuyuaa/RAM)
- (RETA-Grader) Paolo Rosso, Dingqi Yang, Natalia Ostapuk, Philippe Cudré-Mauroux. "RETA: A Schema-Aware, End-to-End Solution for Instance Completion in Knowledge Graphs". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3449883) [*code*](https://github.com/eXascaleInfolab/RETA_code)
- (StAR) Bo Wang, Tao Shen, Guodong Long, Tianyi Zhou, Ying Wang, Yi Chang. "Structure-Augmented Text Representation Learning for Efficient Knowledge Graph Completion". WWW 2021. [*paper*](https://dl.acm.org/doi/10.1145/3442381.3450043) [*code*](https://github.com/wangbo9719/StAR_KGC)

## 2022

### Journal

#### IEEE Transactions on Pattern Analysis and Machine Intelligence

- (HeteHG-VAE) Haoyi Fan, Fengbin Zhang, Yuxuan Wei, Zuoyong Li, Changqing Zou, Yue Gao, Qionghai Dai. "Heterogeneous Hypergraph Variational Autoencoder for Link Prediction". IIEEE Transactions on Pattern Analysis and Machine Intelligence 2022. [*paper*](https://ieeexplore.ieee.org/document/9354594) [*code*](https://github.com/haoyfan/HeteHG-VAE)

#### Information Sciences

- (DA-GCN) Jiarui Zhang, Jian Huang, Jialong Gao, Runhai Han, Cong Zhou. "Knowledge graph embedding by logical-default attention graph convolution neural network for link prediction". Information Sciences 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0020025522001153?via%3Dihub)
- (IKGE) Byungkook Oh, Seungmin Seo, Jimin Hwang, Dongho Lee, Kyong-Ho Lee. "Open-world knowledge graph completion for unseen entities and relations via attentive feature aggregation". Information Sciences 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S002002552101207X?via%3Dihub)
- (OPRL) Pouya Ghiasnezhad Omran, Kerry Taylor, Sergio José Rodríguez Méndez, Armin Haller. "Active knowledge graph completion". Information Sciences 2022. [*paper*](https://www.sciencedirect.com/science/article/pii/S0020025522004479?via%3Dihub)

#### IEEE Transactions on Knowledge and Data Engineering

- (C-RNN) Qiannan Zhu, Xiaofei Zhou, Jianlong Tan, Li Guo. "Knowledge Base Reasoning with Convolutional-Based Recurrent Neural Networks". IEEE Transactions on Knowledge and Data Engineering 2022. [*paper*](https://ieeexplore.ieee.org/document/8890615)
- (KGGen) Hao Chen, Chenwei Zhang, Jun Li, Philip S. Yu, Ning Jing. "KGGen: A Generative Approach for Incipient Knowledge Graph Population". IEEE Transactions on Knowledge and Data Engineering 2022. [*paper*](https://ieeexplore.ieee.org/document/9158381)
- (M-DCN) Zhaoli Zhang, Zhifei Li, Hai Liu, Neal N. Xiong. "Multi-Scale Dynamic Convolutional Network for Knowledge Graph Embedding". IEEE Transactions on Knowledge and Data Engineering 2022. [*paper*](https://ieeexplore.ieee.org/document/9130149) [*code*](https://github.com/zhifei1993/M_DCN)

#### Expert Systems with Applications

- (BTDG) Yujing Lai, Chuan Chen, Zibin Zheng, Yangqing Zhang. "Block term decomposition with distinct time granularities for temporal knowledge graph completion". Expert Systems with Applications 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0957417422004511?via%3Dihub)
- (ComplexGCN) Adnan Zeb, Summaya Saif, Junde Chen, Anwar Ul Haq, Zhiguo Gong, Defu Zhang. "Complex graph convolutional network for link prediction in knowledge graphs". Expert Systems with Applications 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0957417422002548?via%3Dihub)
- (GN+DN) Lu Liu, Jiehang Zeng, Xiaoqing Zheng. "Learning structured embeddings of knowledge graphs with generative adversarial framework". Expert Systems with Applications 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0957417422007138?via%3Dihub)

#### Knowledge Based Systems

- (DKGE) Tianxing Wu, Arijit Khan, Melvin Yong, Guilin Qi, Meng Wang. "Efficiently embedding dynamic knowledge graphs". Knowledge-Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705122005548?via%3Dihub)
- (EIGAT) Yu Zhao, Huali Feng, Han Zhou, Yanruo Yang, Xingyan Chen, Ruobing Xie, Fuzhen Zhuang, Qing Li. "EIGAT: Incorporating global information in local attention for knowledge representation learning". Knowledge-Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121010649?via%3Dihub)
- (HRL) Anjie Zhu, Deqiang Ouyang, Shuang Liang, Jie Shao. "Step by step: A hierarchical framework for multi-hop knowledge graph reasoning with reinforcement learning". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705122004026?via%3Dihub)
- (JointE) Zhehui Zhou, Can Wang, Yan Feng, Defang Chen. "JointE: Jointly utilizing 1D and 2D convolution for knowledge graph embedding". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121011643?via%3Dihub)
- (KANE) Wenqiang Liu, Hongyun Cai, Xu Cheng, Sifa Xie, Yipeng Yu, dukehyzhang. "Learning high-order structural and attribute information by knowledge graph attention networks for enhancing knowledge graph embedding". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705122004853?via%3Dihub)
- (QLogicE) Panfeng Chen, Yisong Wang, Xiaomin Yu, Renyan Feng. "QLogicE: Quantum Logic Empowered Embedding for Knowledge Graph Completion". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121010911?via%3Dihub)
- (ReflectE) Qianjin Zhang, Ronggui Wang, Juan Yang, Lixia Xue. "Knowledge graph embedding by reflection transformation". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121010418?via%3Dihub)
- (RF) Hao Liu, Shu-wang Zhou, Changfang Chen, Tianlei Gao, Jiyong Xu, Minglei Shu. "Dynamic knowledge graph reasoning based on deep reinforcement learning". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705122000697?via%3Dihub)
- (RKG) David Hilman, Ovidiu Serban. "A unified Link Prediction architecture applied on a novel heterogenous Knowledge Base". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/pii/S0950705122000661?via%3Dihub)
- (RLKGE) Lihan Chen, Sihang Jiang, Jingping Liu, Chao Wang, Sheng Zhang, Chenhao Xie, Jiaqing Liang, Yanghua Xiao, Rui Song. "Rule mining over knowledge graphs via reinforcement learning". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S095070512200140X?via%3Dihub)
- (SNS) Md. Kamrul Islam, Sabeur Aridhi, Malika Smaïl-Tabbone. "Negative sampling and rule mining for explainable link prediction in knowledge graphs". KnowledgeBased Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705122005342?via%3Dihub)
- (TuckERT) Pengpeng Shao, Dawei Zhang, Guohua Yang, Jianhua Tao, Feihu Che, Tong Liu. "Tucker decomposition-based temporal knowledge graph completion". Knowledge Based Systems 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0950705121010303?via%3Dihub)

#### Information Processing and Management

- (MHNA) Weishan Cai, Yizhao Wang, Shun Mao, Jieyu Zhan, Yuncheng Jiang. "Multi-heterogeneous neighborhood-aware for Knowledge Graphs alignment". Information Processing and Management 2022. [*paper*](https://www.sciencedirect.com/science/article/pii/S0306457321002685?via%3Dihub) [*code*](https://github.com/cwswork/MHNA)

#### IEEE Intelligent Systems

- (HRL) Zikang Wang, Linjing Li, Daniel Dajun Zeng. "Hierarchical Multihop Reasoning on Knowledge Graphs". IEEE Intelligent Systems 2022. [*paper*](https://ieeexplore.ieee.org/document/9478191)

#### Neurocomputing

- (DensE) Haonan Lu, Hailin Hu, Xiaodong Lin. "DensE: An enhanced noncommutative representation for knowledge graph embedding with adaptive semantic hierarchy". Neurocomputing 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221019342?via%3Dihub)
- (EC) Guanglin Niu, Bo Li, Yongfei Zhang, Yongpan Sheng, Chuan Shi, Jingyang Li, Shiliang Pu. "Joint semantics and data-driven path representation for knowledge graph reasoning". Neurocomputing 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231222001515?via%3Dihub)
- (HSKGCN) Shuanglong Yao, Dechang Pi, Junfu Chen. "Knowledge embedding via hyperbolic skipped graph convolutional networks". Neurocomputing 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231222000546?via%3Dihub)
- (HYPER2) Shiyao Yan, Zequn Zhang, Xian Sun, Guangluan Xu, Li Jin, Shuchao Li. "HYPER2: Hyperbolic embedding for hyper-relational link prediction". Neurocomputing 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231222003940?via%3Dihub)
- (KCGAN) Tehseen Zia, David Windridge. "A generative adversarial network for single and multi-hop distributional knowledge base completion". Neurocomputing 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221009577?via%3Dihub)
- (PEKGE) Yinquan Wang, Yao Chen, Zhe Zhang, Tian Wang. "A probabilistic ensemble approach for knowledge graph embedding". Neurocomputing 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231222007494?via%3Dihub)
- (StructurE) Qianjin Zhang, Ronggui Wang, Juan Yang, Lixia Xue. "Structural contextbased knowledge graph embedding for link prediction". Neurocomputing 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221016192?via%3Dihub)
- (TransMKR) Bojing Hu, Yaqin Ye, Yingqiang Zhong, Jiao Pan, Maosheng Hu. "TransMKR: Translation-based knowledge graph enhanced multi-task point-ofinterest recommendation". Neurocomputing 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0925231221017239?via%3Dihub)

#### Neural Computing and Applications

- (ARPP) Ying Shen, Dagang Li, Du Nan. "Modeling path information for knowledge graph completion". Neural Computing and Applications 2022. [*paper*](https://link.springer.com/article/10.1007/s00521-021-06460-2)

#### Applied Intelligence

- (CTKGC) Jianzhou Feng, Qikai Wei, Jinman Cui, Jing Chen. "Novel translation knowledge graph completion model based on 2D convolution". Applied Intelligence 2022. [*paper*](https://link.springer.com/article/10.1007/s10489-021-02438-8) [*code*](https://github.com/mrweiqk/CTKGC)
- (InterERP) Weidong Li, Rong Peng, Zhi Li. "Improving knowledge graph completion via increasing embedding interactions". Applied Intelligence 2022. [*paper*](https://link.springer.com/article/10.1007/s10489-021-02947-6)
- (JGAN) Jin Huang, Tian Lu, Jia Zhu, Weihao Yu, Tinghua Zhang. "Multi-relational knowledge graph completion method with local information fusion". Applied Intelligence 2022. [*paper*](https://link.springer.com/article/10.1007/s10489-021-02876-4)
- (MMKRL) Xinyu Lu, Lifang Wang, Zejun Jiang, Shichang He, Shizhong Liu. "MMKRL: A robust embedding approach for multi-modal knowledge graph representation learning". Applied Intelligence 2022. [*paper*](https://link.springer.com/article/10.1007/s10489-021-02693-9)
- (RLPath) Ling Chen, Jun Cui, Xing Tang, Yuntao Qian, Yansheng Li, Yongjun Zhang. "RLPath: a knowledge graph link prediction method using reinforcement learning based attentive relation path searching and representation learning". Applied Intelligence 2022. [*paper*](https://link.springer.com/article/10.1007/s10489-021-02672-0)

#### Pattern Recognition Letters

- (CORE) Xiou Ge, Yuncheng Wang, Bin Wang, C.-C. Jay Kuo. "CORE: A knowledge graph entity type prediction method via complex space regression and embedding". Pattern Recognition Letters 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0167865522000897?via%3Dihub)
- (KGBoost) Yuncheng Wang, Xiou Ge, Bin Wang, C.-C. Jay Kuo. "KGBoost: A classification-based knowledge base completion method with negative sampling". Pattern Recognition Letters 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0167865522000939?via%3Dihub)
- (RLKB) Miao Fan, Qiang Zhou, Thomas Fang Zheng, Ralph Grishman. "Distributed representation learning for knowledge graphs with entity descriptions". Pattern Recognition Letters 2022. [*paper*](https://www.sciencedirect.com/science/article/abs/pii/S0167865516302380?via%3Dihub)

### Conference

#### AAAI

- (BoxTE) Johannes Messner, Ralph Abboud, Ismail Ilkan Ceylan. "Temporal Knowledge Graph Completion Using Box Embeddings". AAAI 2022. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/20746)
- (CFAG) Changjian Wang, Xiaofei Zhou, Shirui Pan, Linhua Dong, Zeliang Song, Ying Sha. "Exploring Relational Semantics for Inductive Knowledge Graph Completion". AAAI 2022. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/20337)
- (CURL) Denghui Zhang, Zixuan Yuan, Hao Liu, Xiaodong Lin, Hui Xiong. "Learning to Walk with Dual Agents for Knowledge Graph Reasoning". AAAI 2022. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/20538) [*code*](https://github.com/RutgersDM/DKGR)
- (ER) Zongsheng Cao, Qianqian Xu, Zhiyong Yang, Qingming Huang. "ER: Equivariance Regularizer for Knowledge Graph Completion". AAAI 2022. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/20490) [*code*](https://github.com/Lion-ZS/ER)
- (GIE) Zongsheng Cao, Qianqian Xu, Zhiyong Yang, Xiaochun Cao, Qingming Huang. "Geometry Interaction Knowledge Graph Embeddings". AAAI 2022. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/20491)
- (PU Learning) Jonas Schouterden, Jessa Bekker, Jesse Davis, Hendrik Blockeel. "Unifying Knowledge Base Completion with PU Learning to Mitigate the Observation Bias". AAAI 2022. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/20332) [*code*](https://github.com/ML-KULeuven/KBC-as-PU-Learning)
- (SE-GNN) Ren Li, Yanan Cao, Qiannan Zhu, Guanqun Bi, Fang Fang, Yi Liu, Qian Li. "How Does Knowledge Graph Embedding Extrapolate to Unseen Data: A Semantic Evidence View". AAAI 2022. [*code*](https://github.com/renli1024/SE-GNN)
- (TempoQR) Costas Mavromatis, Prasanna Lakkur Subramanyam, Vassilis N. Ioannidis, Adesoji Adeshina, Phillip R. Howard, Tetiana Grinberg, Nagib Hakim, George Karypis. "TempoQR: Temporal Question Reasoning over Knowledge Graphs". AAAI 2022. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/20526) [*code*](https://github.com/cmavro/TempoQR)
- (TLogic) Yushan Liu, Yunpu Ma, Marcel Hildebrandt, Mitchell Joblin, Volker Tresp."TLogic: Temporal Logical Rules for Explainable Link Forecasting on Temporal Knowledge Graphs". AAAI 2022. [*paper*](https://ojs.aaai.org/index.php/AAAI/article/view/20330) [*code*](https://github.com/liu-yushan/TLogic)

#### ACL

- (AS) Guanglin Niu, Bo Li, Yongfei Zhang, Shiliang Pu. "Knowledge Graph Embedding by Adaptive Limit Scoring Loss Using Dynamic Weighting Strategy". ACL (Findings) 2022. [*paper*](https://aclanthology.org/2022.findings-acl.91/)
- (CAKE) Guanglin Niu, Bo Li, Yongfei Zhang, Shiliang Pu. "CAKE: A Scalable Commonsense-Aware Framework For Multi-View Knowledge Graph Completion". ACL 2022. [*paper*](https://aclanthology.org/2022.acl-long.205/) [*code*](https://github.com/ngl567/CAKE)
- (CEN) Zixuan Li, Saiping Guan, Xiaolong Jin, Weihua Peng, Yajuan Lyu, Yong Zhu, Long Bai, Wei Li, Jiafeng Guo, Xueqi Cheng. "Complex Evolutional Pattern Learning for Temporal Knowledge Graph Reasoning". ACL 2022. [*paper*](https://aclanthology.org/2022.acl-short.32/) [*code*](https://github.com/lee-zix/cen)
- (CogKGE) Zhuoran Jin, Tianyi Men, Hongbang Yuan, Zhitao He, Dianbo Sui, Chenhao Wang, Zhipeng Xue, Yubo Chen, Jun Zhao. "CogKGE: A Knowledge Graph Embedding Toolkit and Benchmark for Representing Multi-source and Heterogeneous Knowledge". ACL (demo) 2022. [*paper*](https://aclanthology.org/2022.acl-demo.16/) [*code*](https://github.com/jinzhuoran/cogkge)
- (GenderBias) Yupei Du, Qi Zheng, Yuanbin Wu, Man Lan, Yan Yang, Meirong Ma. "Understanding Gender Bias in Knowledge Base Embeddings". ACL 2022. [*paper*](https://aclanthology.org/2022.acl-long.98/)
- (KGT5) Apoorv Saxena, Adrian Kochsiek, Rainer Gemulla. "Sequence-to-Sequence Knowledge Graph Completion and Question Answering". ACL 2022. [*paper*](https://aclanthology.org/2022.acl-long.201/) [*code*](https://github.com/apoorvumang/kgt5)
- (MEKER) Viktoria Chekalina, Anton Razzhigaev, Albert Sayapin, Evgeny Frolov, Alexander Panchenko. "MEKER: Memory Efficient Knowledge Embedding Representation for Link Prediction and Question Answering". ACL (student) 2022. [*paper*](https://aclanthology.org/2022.acl-srw.27/)
- (PKGC) Xin Lv, Yankai Lin, Yixin Cao, Lei Hou, Juanzi Li, Zhiyuan Liu, Peng Li, Jie Zhou. "Do Pre-trained Models Benefit Knowledge Graph Completion? A Reliable Evaluation and a Reasonable Approach". ACL (Findings) 2022. [*paper*](https://aclanthology.org/2022.findings-acl.282/) [*code*](https://github.com/thu-keg/pkgc)
- (RotateQVS) Kai Chen, Ye Wang, Yitong Li, Aiping Li. "RotateQVS: Representing Temporal Information as Rotations in Quaternion Vector Space for Temporal Knowledge Graph Completion". ACL 2022. [*paper*](https://aclanthology.org/2022.acl-long.402/)
- (SimKGC) Liang Wang, Wei Zhao, Zhuoyu Wei, Jingming Liu. "SimKGC: Simple Contrastive Knowledge Graph Completion with Pre-trained Language Models". ACL 2022. [*paper*](https://aclanthology.org/2022.acl-long.295/) [*code*](https://github.com/intfloat/SimKGC)
- (SS-AGA) Zijie Huang, Zheng Li, Haoming Jiang, Tianyu Cao, Hanqing Lu, Bing Yin, Karthik Subbian, Yizhou Sun, Wei Wang. "Multilingual Knowledge Graph Completion with Self-Supervised Adaptive Graph Alignment". ACL 2022. [*paper*](https://aclanthology.org/2022.acl-long.36/) [*code*](https://github.com/amzn/ss-aga-kgc)

#### ICML

- (NSloss) Hidetaka Kamigaito, Katsuhiko Hayashiu. "Comprehensive Analysis of Negative Sampling in Knowledge Graph Representation Learning". ICML 2022. [*paper*](https://proceedings.mlr.press/v162/kamigaito22a.html)
- (GNN-QE) Zhaocheng Zhu, Mikhail Galkin, Zuobai Zhang, Jian Tang. "NeuralSymbolic Models for Logical Queries on Knowledge Graphs". ICML 2022. [*paper*](https://proceedings.mlr.press/v162/zhu22c.html)
- (HousE) Rui Li, Jianan Zhao, Chaozhuo Li, Di He, Yiqi Wang, Yuming Liu, Hao Sun, Senzhang Wang, Weiwei Deng, Yanming Shen, Xing Xie, Qi Zhang. "HousE: Knowledge Graph Embedding with Householder Parameterization". ICML 2022. [*paper*](https://proceedings.mlr.press/v162/li22ab.html) [*code*](https://github.com/rui9812/HousE)

#### IJCAI

- (Adversarial Explanations) Patrick Betz, Christian Meilicke, Heiner Stuckenschmidt. "Adversarial Explanations for Knowledge Graph Embeddings". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/391)
- (KGA) Jiang Wang, Filip Ilievski, Pedro A. Szekely, Ke-Thia Yao. "Augmenting Knowledge Graphs for Better Link Prediction". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/316)
- (MEIM) Hung Nghiep Tran, Atsuhiro Takasu. "MEIM: Multi-partition Embedding Interaction Beyond Block Term Format for Efficient and Expressive Link Prediction". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/314) [*code*](https://github.com/tranhungnghiep/MEIM-KGE)
- (PUDA) Zhenwei Tang, Shichao Pei, Zhao Zhang, Yongchun Zhu, Fuzhen Zhuang, Robert Hoehndorf, Xiangliang Zhang. "Positive-Unlabeled Learning with Adversarial Data Augmentation for Knowledge Graph Completion". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/312) [*code*](https://github.com/lilv98/PUDA-IJCAI22)
- (REP) Huijuan Wang, Siming Dai, Weiyue Su, Hui Zhong, Zeyang Fang, Zhengjie Huang, Shikun Feng, Zeyu Chen, Yu Sun, Dianhai Yu. "Simple and Effective Relationbased Embedding Propagation for Knowledge Representation Learning". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/382) [*code*](https://github.com/PaddlePaddle/PGL/tree/d5f31784b1b6f2d5117537908acde6625b9abeef/apps/Graph4KG/examples/REP)
- (rGalT) Yifu Gao, Linhui Feng, Zhigang Kan, Yi Han, Linbo Qiao, Dongsheng Li. "Modeling Precursors for Temporal Knowledge Graph Reasoning via Autoencoder Structure". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/284)
- (SNRI) Xiaohan Xu, Peng Zhang, Yongquan He, Chengpeng Chao, Chaoyang Yan. "Subgraph Neighboring Relations Infomax for Inductive Link Prediction on Knowledge Graphs". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/325)
- (TEMP) Zhiwei Hu, Victor Gutiérrez-Basulto, Zhiliang Xiang, Xiaoli Li, Ru Li, Jeff Z. Pan. "Type-aware Embeddings for Multi-Hop Reasoning over Knowledge Graphs". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/427) [*code*](https://github.com/zhiweihu1103/QE-TEMP) [*code*](https://github.com/SXUNLP/QE-TEMP)
- (TiRGN) Yujia Li, Shiliang Sun, Jing Zhao. "TiRGN: Time-Guided Recurrent Graph Network with Local-Global Historical Patterns for Temporal Knowledge Graph Reasoning". IJCAI 2022. [*paper*](https://www.ijcai.org/proceedings/2022/299) [*code*](https://github.com/Liyyy2122/TiRGN)

#### NAACL-HLT

- (LDP) Huda Hakami, Mona Hakami, Angrosh Mandya, Danushka Bollegala. "Learning to Borrow- Relation Representation for Without-Mention Entity-Pairs for Knowledge Graph Completion". NAACL-HLT 2022. [*paper*](https://aclanthology.org/2022.naacl-main.209/) [*code*](https://github.com/huda-hakami/learning-to-borrow-for-kgs)
- (Query2Particles) Jiaxin Bai, Zihao Wang, Hongming Zhang, Yangqiu Song. "Query2Particles: Knowledge Graph Reasoning with Particle Embeddings". NAACL-HLT (Findings) 2022. [*paper*](https://aclanthology.org/2022.findings-naacl.207/) [*code*](https://github.com/hkust-knowcomp/query2particles)
- (StATIK) Elan Markowitz, Keshav Balasubramanian, Mehrnoosh Mirtaheri, Murali Annavaram, Aram Galstyan, Greg Ver Steeg. "*StATIK: Structure and Text for Inductive Knowledge Graph Completion*\*". NAACL-HLT (Findings) 2022. [*paper*](https://aclanthology.org/2022.findings-naacl.46/)

#### SIGMOD

- (CompactWalks) Pei-Yu Hou, Daniel Robert Korn, Cleber C. Melo-Filho, David R. Wright, Alexander Tropsha, Rada Chirkova. "Compact Walks: Taming KnowledgeGraph Embeddings with Domain- and Task-Specific Pathways". SIGMOD 2022. [*paper*](https://dl.acm.org/doi/10.1145/3514221.3517903) [*code*](https://github.com/DnlRKorn/sg_regex)
- (Kelpie) Andrea Rossi, Donatella Firmani, Paolo Merialdo, Tommaso Teofili. "Explaining Link Prediction Systems based on Knowledge Graph Embeddings". SIGMOD 2022. [*paper*](https://dl.acm.org/doi/10.1145/3514221.3517887)

#### ICDE

- (Evoda) Lianlong Wu, Emanuel Sallinger, Evgeny Sherkhonov, Sahar Vahdati, Georg Gottlob. "Rule Learning over Knowledge Graphs with Genetic Logic Programming". ICDE 2022. [*paper*](https://ieeexplore.ieee.org/document/9835403)
- (HET-KG) Sicong Dong, Xupeng Miao, Pengkai Liu, Xin Wang, Bin Cui, Jianxin Li. "HET-KG: Communication-Efficient Knowledge Graph Embedding Training via Hotness-Aware Cache". ICDE 2022. [*paper*](https://ieeexplore.ieee.org/document/9835364) [*code*](https://github.com/RweBs/HotKE)

#### SIGIR

- (ConGLR) Qika Lin, Jun Liu, Fangzhi Xu, Yudai Pan, Yifan Zhu, Lingling Zhang, Tianzhe Zhao. "Incorporating Context Graph with Logical Reasoning for Inductive Relation Prediction". SIGIR 2022. [*paper*](https://dl.acm.org/doi/10.1145/3477495.3531996)
- (KGC Sparsity) Ying Zhou, Xuanang Chen, Ben He, Zheng Ye, Le Sun. "Re-thinking Knowledge Graph Completion Evaluation from an Information Retrieval Perspective". SIGIR 2022. [*paper*](https://dl.acm.org/doi/10.1145/3477495.3532052) [*code*](https://github.com/zhouying20/kgc-sparsity)
- (MKGformer) Xiang Chen, Ningyu Zhang, Lei Li, Shumin Deng, Chuanqi Tan, Changliang Xu, Fei Huang, Luo Si, Huajun Chen. "Hybrid Transformer with Multilevel Fusion for Multimodal Knowledge Graph Completion". SIGIR 2022. [*paper*](https://dl.acm.org/doi/10.1145/3477495.3531992) [*code*](https://github.com/zjunlp/MKGformer)
- (MorsE) Mingyang Chen, Wen Zhang, Yushan Zhu, Hongting Zhou, Zonggang Yuan, Changliang Xu, Huajun Chen. "Meta-Knowledge Transfer for Inductive Knowledge Graph Embedding". SIGIR 2022. [*paper*](https://dl.acm.org/doi/10.1145/3477495.3531757) [*code*](https://github.com/zjukg/MorsE)
- (NeuralKG) Wen Zhang, Xiangnan Chen, Zhen Yao, Mingyang Chen, Yushan Zhu, Hongtao Yu, Yufeng Huang, Yajing Xu, Ningyu Zhang, Zezhong Xu, Zonggang Yuan, Feiyu Xiong, Huajun Chen. "NeuralKG: An Open Source Library for Diverse Representation Learning of Knowledge Graphs". SIGIR 2022. [*paper*](https://dl.acm.org/doi/10.1145/3477495.3531669) [*code*](https://github.com/zjukg/NeuralKG)

#### WSDM

- (AttEt) Jianhuan Zhuo, Qiannan Zhu, Yinliang Yue, Yuhong Zhao, Weisi Han. "A Neighborhood-Attention Fine-grained Entity Typing for Knowledge Graph Completion". WSDM 2022. [*paper*](https://dl.acm.org/doi/10.1145/3488560.3498395)
- (DualDE) Yushan Zhu, Wen Zhang, Mingyang Chen, Hui Chen, Xu Cheng, Wei Zhang, Huajun Chen. "DualDE: Dually Distilling Knowledge Graph Embedding for Faster and Cheaper Reasoning". WSDM 2022. [*paper*](https://dl.acm.org/doi/10.1145/3488560.3498437) [*code*](https://github.com/YushanZhu/DistilE)
- (EvoKG) Namyong Park, Fuchen Liu, Purvanshi Mehta, Dana Cristofor, Christos Faloutsos, Yuxiao Dong. "EvoKG: Jointly Modeling Event Time and Network Structure for Reasoning over Temporal Knowledge Graphs". WSDM 2022. [*paper*](https://dl.acm.org/doi/10.1145/3488560.3498451) [*code*](https://github.com/NamyongPark/EvoKG)
- (NoGE) Dai Quoc Nguyen, Vinh Tong, Dinh Q. Phung, Dat Quoc Nguyen. "Node Cooccurrence based Graph Neural Networks for Knowledge Graph Link Prediction". WSDM 2022. [*paper*](https://dl.acm.org/doi/10.1145/3488560.3502183) [*code*](https://github.com/daiquocnguyen/GNN-NoGE)

#### DASFAA

- (ARIM-TE) Tingyi Zhang, Zhixu Li, Jiaan Wang, Jianfeng Qu, Lin Yuan, An Liu, Lei Zhao, Zhigang Chen. "Aligning Internal Regularity and External Influence of Multigranularity for Temporal Knowledge Graph Embedding". DASFAA 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-00129-1_10)
- (CoCuKGR) Dan Shi, Anchen Li, Bo Yang. "Counterfactual-Guided and Curiosity- Driven Multi-hop Reasoning over Knowledge Graph". DASFAA 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-00123-9_13) 
- (ExKGR) Cheng Yan, Feng Zhao, Hai Jin. "ExKGR: Explainable Multi-hop Reasoning for Evolving Knowledge Graph". DASFAA 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-00123-9_11)
- (FactE) Xin Lv, Jiaxin Shi, Shulin Cao, Lei Hou, Juanzi Li. "Triple-as-Node Knowledge Graph and Its Embeddings". DASFAA 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-00123-9_8) 
- (Sensitivity) Han Yang, Leilei Zhang, Fenglong Su, Jinhui Pang. "What Affects the Performance of Models? Sensitivity Analysis of Knowledge Graph Embedding". DASFAA 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-00123-9_55)
- (TRHyTE) Lin Yuan, Zhixu Li, Jianfeng Qu, Tingyi Zhang, An Liu, Lei Zhao, Zhigang Chen. "TRHyTE: Temporal Knowledge Graph Embedding Based on Temporal-Relational Hyperplanes". DASFAA 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-00123-9_10)

#### ESWC

- (Aggregation) Patrick Betz, Christian Meilicke, Heiner Stuckenschmidt. "Supervised Knowledge Aggregation for Knowledge Graph Completion". ESWC 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-06981-9_5)
- (RACE2T) Changlong Zou, Jingmin An, Guanyu Li. "Knowledge Graph Entity Type Prediction with Relational Aggregation Graph Attention Network". ESWC 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-06981-9_3)
- (ST-KGE) Mojtaba Nayyeri, Sahar Vahdati, Md Tansen Khan, Mirza Mohtashim Alam, Lisa Wenige, Andreas Behrend, Jens Lehmann. "Dihedron Algebraic Embeddings for Spatio-Temporal Knowledge Graph Completion". ESWC 2022. [*paper*](https://link.springer.com/chapter/10.1007/978-3-031-06981-9_15)

#### WWW

- (DiriE) Feiyang Wang, Zhongbao Zhang, Li Sun, Junda Ye, Yang Yan. "DiriE: Knowledge Graph Embedding with Dirichlet Distribution". WWW 2022. [*paper*](https://dl.acm.org/doi/10.1145/3485447.3512028)
- (GCN4KGC) Zhanqiu Zhang, Jie Wang, Jieping Ye, Feng Wu. "Rethinking Graph Convolutional Networks in Knowledge Graph Completion". WWW 2022. [*paper*](https://dl.acm.org/doi/10.1145/3485447.3511923) [*code*](https://github.com/MIRALab-USTC/GCN4KGC) 
- (HaLE) Kai Wang, Yu Liu, Quan Z. Sheng. "Swift and Sure: Hardness-aware Contrastive Learning for Low-dimensional Knowledge Graph Embeddings". WWW 2022. [*paper*](https://dl.acm.org/doi/10.1145/3485447.3511927)
- (RED-GNN) Yongqi Zhang, Quanming Yao. "Knowledge Graph Reasoning with Relational Digraph". WWW 2022. [*paper*](https://dl.acm.org/doi/10.1145/3485447.3512008) [*code*](https://github.com/AutoML-Research/RED-GNN)
- (SelfKG) Xiao Liu, Haoyun Hong, Xinghao Wang, Zeyi Chen, Evgeny Kharlamov, Yuxiao Dong, Jie Tang. "SelfKG: Self-Supervised Entity Alignment in Knowledge Graphs". WWW 2022. [*paper*](https://dl.acm.org/doi/10.1145/3485447.3511945) [*code*](https://github.com/THUDM/SelfKG)
- (TKGC) Jiacheng Huang, Yao Zhao, Wei Hu, Zhen Ning, Qijin Chen, Xiaoxia Qiu, Chengfu Huo, Weijun Ren. "Trustworthy Knowledge Graph Completion Based on Multi-sourced Noisy Datas". WWW 2022. [*paper*](https://dl.acm.org/doi/10.1145/3485447.3511938) [*code*](https://github.com/nju-websoft/TKGC)

#### ICASSP

- (SGI) Heeyoung Kwak, Hyunkyung Bae, Kyomin Jung. **"Subgraph RepresentationLearning with Hard Negative Samples for Inductive Link Prediction"**. ICASSP 2022. [*paper*](https://ieeexplore.ieee.org/document/9747485)

### Focus

#### IEEE Transactions on Pattern Analysis and Machine Intelligence

- (PyKEEN) Mehdi Ali, Max Berrendorf, Charles Tapley Hoyt, Laurent Vermue, MikhailGalkin, Sahand Sharifzadeh, Asja Fischer, Volker Tresp, Jens Lehmann. **"Bringing Light Into the Dark: A Large-scale Evaluation of Knowledge Graph Embedding Models Under a Unified Framework". IEEE Transactions on Pattern Analysis and Machine Intelligence.** [*paper*](https://arxiv.org/abs/2006.13365) [*code*](https://github.com/pykeen/pykeen) [*benchmark*](https://github.com/pykeen/benchmarking)
