# BLSTDoc
### BLAST 2.10.0+ 查询方法参数描述

### 可选参数

- -h
  - 打印用法和描述，忽略其他入参

- -help
  - 打印用法，描述和参数，忽略其他入参

- -version
  - 打印当前版本号，忽略其他参数

### 查询可选项

- -query <File_In>
  - 输入文件名称
  - 默认是 ‘-’

- -query_loc  <String>
  - 查询在序列是偏移的位置（格式是：start-stop)

- -strand <String,'both','minus','plus'>
  - 根据数据库去查询strands
  - 默认是‘both’

- query_gencode <Integer,values between:1-6,9-16,21-31,33>
  - 遗传密码用来翻译查询(seehttps://www.ncbi.nlm.nih.gov/Taxonomy/taxonomyhome.html/index.cgi?chapter=
    cgencodes for details)
  - 默认是‘1’

###  搜索可选参数

- -task <string,Permissible value:'blastx' 'blastx-fast'>
  - 要执行的任务
  - 默认是‘blastx’

- -db <Sting>
  - BLAST 数据库的名称
  - *不能同时与：subject，subject_loc同时使用

- -out <Sting>
  - 输出文件名称
  - 默认是‘-’

- eval <Real>
  - 要保存的期望阈值
  - 默认是‘10’

- -word_size <Integer,>=2>
  - 文字查找算法中词的大小

- -gapopen <Integer>
  - 空位开放罚分
  - 默认是‘0分’

- -gapextend <Integer>
  - 空位拓展罚分
  - 默认是‘0分’

- -max_intron_length <Integer, >=0>
  - 当链接多条不同的路线时，翻译核苷酸序列中允许的最大内含子长度
  - 默认是‘0’

- -matrix <String>
  - 评分矩阵的名字(一般用 BLOSUM62)

- threshould <Real,>=0>
  - 将单词添加到BLAST查找表中的最小单词分数

- -comp_based_stats <String>

  - 使用基于组合的统计
    - D or d : 默认值（相当于2）
    - 0 or F or f : 没有基于组合的统计信息
    - 1 : NAR 29:2994-30052001中基于成分的统计
    - 2 or T or t : 生物信息学中基于成分的分数调整21:902-911，2005年，以序列属性为条件
    - 3 : 生物信息学21:902-911中基于成分的分数调整，2005年，无条件

  - 默认是‘2’

### BLAST-2-Sequences 的可选参数

- -subject <File_In>
  - *不能与：db, gilist, seqidlist, negative_gilist,
    negative_seqidlist, taxids, taxidlist, negative_taxids, negative_taxidlist,
    ipglist, negative_ipglist, db_soft_mask, db_hard_mask一起使用
- -subject_loc <String>
  - *不能与：db, gilist, seqidlist, negative_gilist,
    negative_seqidlist, taxids, taxidlist, negative_taxids, negative_taxidlist,
    ipglist, negative_ipglist, db_soft_mask, db_hard_mask, remote 一起使用

### 格式化可选参数

- -outfmt <String>

  - 输出视图参数

    | 名称 | 含义                    |
    | :--: | ----------------------- |
    |  0   | 成对                    |
    |  1   | 锚定的显示身份查询      |
    |  2   | 查询锚定无标识          |
    |  3   | 定位显示表示平面查询    |
    |  4   | 平面查询没有锚定标识    |
    |  5   | BLAST XML               |
    |  6   | 表格                    |
    |  7   | 带注释行的表格          |
    |  8   | 序列对齐（文本ASN.1）   |
    |  9   | Seqalign（二进制ASN.1） |
    |  10  | 逗号分隔值              |
    |  11  | BLAST档案（ASN.1）      |
    |  12  | Seqalign（JSON）格式    |
    |  13  | 多文件BLAST JSON        |
    |  14  | 多文件BLAST XML2        |
    |  15  | 单个文件BLAST JSON      |
    |  16  | 单个文件BLAST XML2      |
    |  18  | 有机体报告              |

       - 选项6、7和10还可以配置为由空格分隔的格式说明符指定的自定义格式，或者由delim关键字指定的标记。

         - E.g.: "10 delim=@ qacc sacc score".

       - 参数为:

         | 名称        | 含义                                                         |
         | ----------- | ------------------------------------------------------------ |
         | qseqid      | 查询Seq-id                                                   |
         | ggi         | 查询 GI                                                      |
         | qacc        | 查询accesion                                                 |
         | qaccver     | 查询accesion 和version                                       |
         | qlen        | 查询 序列长度（sequence） 长度                               |
         | sseqid      | 查询subject Seq-id                                           |
         | sallseqid   | 查询所有subject Seq-id(s) ，用'' ; ''分割                    |
         | sgi         | Subject GI                                                   |
         | sallgi      | 所有的Subject GIs                                            |
         | sacc        | Subject accession                                            |
         | saccver     | Subject accession.version                                    |
         | sallacc     | All subject accessions                                       |
         | slen        | Subject sequence length                                      |
         | qstart      | Start of alignment in query                                  |
         | qend        | End of alignment in query                                    |
         | sstart      | Start of alignment in subject                                |
         | send        | End of alignment in subject                                  |
         | qseq        | 查询序列对齐                                                 |
         | sseq        | Subject 序列对齐                                             |
         | evalue      | 期望值 expect value                                          |
         | bitscore    | bit 分数 bit score                                           |
         | score       | 原始分数 raw score                                           |
         | length      | 长度 alignment length                                        |
         | pident      | 相同匹配的百分比 Percentage of identical matches             |
         | nident      | 相同匹配数值 Number of identical matches                     |
         | mismatch    | 不匹配的数量 Number of mismatches                            |
         | positive    | 正得分匹配的次数 Number of mismatches                        |
         | gapopen     | 间隙开口数量  Number of gap openings                         |
         | gaps        | 间隙总数 Total number of gaps                                |
         | ppos        | 匹配为正百分比 Percentage of positive-scoring matches        |
         | frames      | 查询和 Subject的用/分割的框架  Query  and subject frames separated by a '/' |
         | qframe      | Query frame                                                  |
         | sframe      | Subject frame                                                |
         | btop        | BLAST 回溯操作 Blast traceback operations (BTOP)             |
         | staxid      | Subject Taxonomy ID                                          |
         | ssciname    | Subject Scientific Name                                      |
         | scomname    | Subject Common Name                                          |
         | sblastname  | Subject Blast Name                                           |
         | sskingdom   | Subject Super Kingdom                                        |
         | staxids     | unique Subject Taxonomy ID(s), separated by a ';'            |
         | sscinames   | nique Subject Scientific Name(s), separated by a ';'         |
         | scomnames   | unique Subject Common Name(s), separated by a ';'            |
         | sblastnames | unique Subject Blast Name(s), separated by a ';'             |
         | sskingdoms  | unique Subject Super Kingdom(s), separated by a ';'          |
         | stitle      | Subject Title                                                |
         | salltitles  | All Subject Title(s), separated by a '<>'                    |
         | sstrand     | Subject Strand                                               |
         | qcovs       | Query Coverage Per Subject                                   |
         | qcovhsp     | Query Coverage Per HSP                                       |
         | qcovus      | Coverage Per Unique Subject (blastn only)                    |

    - 当不提供时，默认值如下：

      - 'qaccver saccver pident length mismatch gapopen qstart qend sstart send
        evalue bitscore', which is equivalent to the keyword 'std'
      - 默认是‘0’

- -show_gis

- 显示NCBI GIs 描述 Show NCBI GIs in deflines

- num_descriptions <Integer,>0>

  - 显示 行描述的数据库序列的数量
  - 不适应与 outfmt >4
  - 默认是‘500’

- -num_alignments 

  - 显示路线的数据库序列数
  - 默认是‘250’

- -line_length<Integer ,>=0>

  - 一行显示的数据的最大长度
  - 不适应与 outfmt >4
  - 默认是‘60’

- -html 

- 生成html输出

- -sorthits <Integer, (>=0 and =<4)>

  - 根据命中的次数排序

  - sort by参数有：

    | 参数 | 含义             |
    | ---- | ---------------- |
    | 0    | evalue           |
    | 1    | bit score        |
    | 2    | Total score      |
    | 3    | percent identity |
    | 4    | query coverage   |

    - 不适应与 outfmt >4

- -sorthps <Integer, (>=0 and =<4)>

  - 根据hps排序

  - sort by参数有：

    | 参数 | 含义                 |
    | ---- | -------------------- |
    | 0    | hps evalue           |
    | 1    | hps bit score        |
    | 2    | hps Total score      |
    | 3    | hps percent identity |
    | 4    | hps query coverage   |

    ​    

### 查询过滤参数

- -seg  <String>

  -   Filter query sequence with SEG (Format: 'yes', 'window locut hicut', or 'no' to disable)
  -   Default = '12 2.2 2.5'

 - soft_masking <Boolen>

   - Apply filtering locations as soft masks
   - Default = `false'

   - lcase_masking
     - Use lower case filtering in query and subject sequence(s)

    ### 限定查询和结果

- -gilist <String>

  - Restrict search of database to list of GIs
  - *Incompatible with:  seqidlist, taxids, taxidlist, negative_gilist,negative_seqidlist, negative_taxids, negative_taxidlist, remote, subject,
  - subject_loc

- -seqidlist <String>

  - Restrict search of database to list of SeqIDs
  - *Incompatible with:  gilist, taxids, taxidlist, negative_gilist,negative_seqidlist, negative_taxids, negative_taxidlist, remote, subject,
  - subject_loc

- -negative_gilist <String>

  - Restrict search of database to everything except the specified GIs
  - *Incompatible with:  gilist, seqidlist, taxids, taxidlist,negative_seqidlist, negative_taxids, negative_taxidlist, remote, subject,
  - subject_loc

- -negative_seqidlist <String>

  - Restrict search of database to everything except the specified SeqIDs
  - *Incompatible with:  gilist, seqidlist, taxids, taxidlist,negative_gilist, negative_taxids, negative_taxidlist, remote, subject,
  - subject_loc

- -taxids <String>

  - Restrict search of database to include only the specified taxonomy IDs(multiple IDs delimited by ',')
  - *Incompatible with:  gilist, seqidlist, taxidlist, negative_gilist,negative_seqidlist, negative_taxids, negative_taxidlist, remote, subject,
  - subject_loc

- -negative_taxids <String>

  - Restrict search of database to everything except the specified taxonomy IDs(multiple IDs delimited by ',')
  - *Incompatible with:  gilist, seqidlist, taxids, taxidlist,negative_gilist, negative_seqidlist, negative_taxidlist, remote, subject,
  - subject_loc

- -taxidlist <String>

  - Restrict search of database to include only the specified taxonomy IDs
  - *Incompatible with:  gilist, seqidlist, taxids, negative_gilist,negative_seqidlist, negative_taxids, negative_taxidlist, remote, subject,
  - subject_loc

- -negative_taxidlist <String>

  - Restrict search of database to everything except the specified taxonomy IDs
  - *Incompatible with:  gilist, seqidlist, taxids, taxidlist,negative_gilist, negative_seqidlist, negative_taxids, remote, subject,
  - subject_loc

- -ipglist <String>

  - Restrict search of database to list of IPGs
  - *Incompatible with:  subject, subject_loc

- -negative_ipglist <String>

  - Restrict search of database to everything except the specified IPGs
  - *Incompatible with:  subject, subject_loc

- -entrez_query <String>

  - Restrict search with the given Entrez query
  - *Requires:  remote

- -db_soft_mask <String>

  - Filtering algorithm ID to apply to the BLAST database as soft masking
  - *Incompatible with:  db_hard_mask, subject, subject_loc

- -db_hard_mask <String>

  - Filtering algorithm ID to apply to the BLAST database as hard masking
  - *Incompatible with:  db_soft_mask, subject, subject_loc

- -qcov_hsp_perc <Real, 0..100>

  - Percent query coverage per hsp

- -max_hsps <Integer, >=1>

  - Set maximum number of HSPs per subject sequence to save for each query

- -culling_limit <Integer, >=0>

  - If the query range of a hit is enveloped by that of at least this many higher-scoring hits, delete the hit
   - *Incompatible with:  best_hit_overhang, best_hit_score_edge

- -best_hit_overhang <Real, (>0 and <0.5)>

  - Best Hit algorithm overhang value (recommended value: 0.1)
  - *Incompatible with:  culling_limit

- -best_hit_score_edge <Real, (>0 and <0.5)>

  - Best Hit algorithm score edge value (recommended value: 0.1)
  - *Incompatible with:  culling_limit

- -subject_besthit

  - Turn on best hit per subject sequence

- -max_target_seqs <Integer, >=1>

  - Maximum number of aligned sequences to keep(value of 5 or more is recommended)
  - Default = `500'
  - *Incompatible with:  num_descriptions, num_alignments

### Statistical options

- -dbsize <Int8>
  - Effective length of the database
- -searchsp <Int8, >=0>
  - Effective length of the search space
- -sum_stats <Boolean>
  - Use sum statistics

### Search strategy options

- -import_search_strategy <File_In>
  - Search strategy to use
  - * Incompatible with:  export_search_strategy
- -export_search_strategy <File_Out>
  - File name to record the search strategy used
  - * Incompatible with:  import_search_strategy

### Extension options

- -xdrop_ungap <Real>
  - X-dropoff value (in bits) for ungapped extensions
- -xdrop_gap <Real>
  - X-dropoff value (in bits) for preliminary gapped extensions
- -xdrop_gap_final <Real>
  - X-dropoff value (in bits) for final gapped alignment
- -window_size <Integer, >=0>
  - Multiple hits window size, use 0 to specify 1-hit algorithm
- -ungapped
  - Perform ungapped alignment only?

### Miscellaneous options

- -parse_deflines
  -Should the query and subject defline(s) be parsed?
- -num_threads <Integer, >=1>
  - Number of threads (CPUs) to use in the BLAST search
  - Default = `1'
  - * Incompatible with:  remote
- -remote
  - Execute search remotely?
  - * Incompatible with:  gilist, seqidlist, taxids, taxidlist,negative_gilist, negative_seqidlist, negative_taxids, negative_taxidlist,subject_loc, num_threads
- -use_sw_tback
  - Compute locally optimal Smith-Waterman alignments

