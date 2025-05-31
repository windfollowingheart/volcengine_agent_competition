## 功能介绍

**论文引言和相关工作撰写智能体** 包含如下功能：

### 1. 论文批量检索和知识提取
 - 用户输入想要调研的关键词，智能体会根据关键词进行文献检索，并对检索到的文献进行摘要、引言和相关工作部分的知识提取。
 - 用户可自定义每个关键词的检索文献数量(默认是每个关键词检索10篇文献)，任务运行时长与检索文献数量成正相关。
 - 用户可通过设置邮箱地址触发任务结束通知，而不必一直等待。邮件中将会附加提取的知识列表作为附件，为`.json`后缀的文件，用户需自行保存该文件。
 - 用户可在后续的文献综述撰写功能中将该功能提取到的知识作为输入。

该功能输出示例如下：
```json
[
    {
        "title": "文献标题",
        "abstract": "文献摘要",
        "url": "文献链接",
        "published_date": "发表日期",
        "authors": ["作者1", "作者2"],
        {
            "induction": {
                "research_objective": "研究属于视频插值领域，针对现有视频插值方法在起始帧和结束帧差异较大时难以生成合理插值，且现有视频扩散模型未充分利用起始帧和结束帧条件信息的问题，旨在开发基于扩散模型的视频插值方法，克服现有模型局限性，提升视频插值质量，推动相关应用发展。",
                "innovation_points": "1. 开发级联视频插值扩散模型VIDIM，能在两个输入帧之间生成高质量视频；2. 对VIDIM的设计选择进行消融实验，证明参数共享处理条件帧和使用无分类器引导的重要性；3. 提出针对生成帧插值的两个精心策划的困难数据集Davis - 7和UCF101 - 7；4. 在困难插值问题上，VIDIM相比现有最先进方法在生成模型指标上总体取得更好结果，且在定性评估中更受用户青睐。"
            },
            "related_work": [
                {
                    "class_name": "传统视频帧插值方法",
                    "class_description": "基于特征提取、对应估计、图像变形和帧合成等步骤的视频帧插值方法，常依赖线性或明确的运动假设。",
                    "related_work_items": [
                        {
                            "article_info": {
                                "title": "Real-time intermediate flow estimation for video frame interpolation",
                                "authors": ["Zhewei Huang", "Tianyuan Zhang", "Wen Heng", "Boxin Shi", "Shuchang Zhou"],
                                "year": 2022,
                                "conference": "Proceedings of the European Conference on Computer Vision (ECCV)",
                                "journal": "",
                                "url": "",
                                "doi": ""
                            },
                            "key_method_technology": "实时中间流估计",
                            "performance_improvement": "实现视频帧的实时插值",
                            "limitation": "在输入帧差异大、运动复杂或模糊时难以生成合理插值"
                        },
                        {
                            "article_info": {
                                "title": "AMT: Allpairs multi-field transforms for efficient frame interpolation",
                                "authors": ["Zhen Li", "Zuo-Liang Zhu", "Ling-Hao Han", "Qibin Hou", "Chun-Le Guo", "Ming-Ming Cheng"],
                                "year": 2023,
                                "conference": "IEEE Conference on Computer Vision and Pattern Recognition (CVPR)",
                                "journal": "",
                                "url": "",
                                "doi": ""
                            },
                            "key_method_technology": "全对多场变换",
                            "performance_improvement": "提高帧插值效率",
                            "limitation": "在输入帧差异大、运动复杂或模糊时难以生成合理插值"
                        },
                        {
                            "article_info": {
                                "title": "Film: Frame interpolation for large motion",
                                "authors": ["Fitsum Reda", "Janne Kontkanen", "Eric Tabellion", "Deqing Sun", "Caroline Pantofaru", "Brian Curless"],
                                "year": 2022,
                                "conference": "European Conference on Computer Vision (ECCV)",
                                "journal": "",
                                "url": "",
                                "doi": ""
                            },
                            "key_method_technology": "针对大运动的帧插值",
                            "performance_improvement": "在一定程度上处理大运动的帧插值",
                            "limitation": "在输入帧差异大、运动复杂或模糊时难以生成合理插值"
                        }
                    ]
                },
                {
                    "class_name": "基于扩散模型的视频帧插值方法",
                    "class_description": "利用扩散模型进行视频帧插值的方法，尝试解决传统方法的局限性。",
                    "related_work_items": [
                        {
                            "article_info": {
                                "title": "LDMVFI: Video frame interpolation with latent diffusion models",
                                "authors": ["Duolikun Danier", "Fan Zhang", "David Bull"],
                                "year": 2023,
                                "conference": "",
                                "journal": "",
                                "url": "arXiv preprint arXiv:2303.09508",
                                "doi": ""
                            },
                            "key_method_technology": "使用潜在扩散模型进行视频帧插值",
                            "performance_improvement": "引入扩散模型解决视频帧插值问题",
                            "limitation": "未明确提及局限性"
                        },
                        {
                            "article_info": {
                                "title": "Video diffusion models",
                                "authors": ["Jonathan Ho", "Tim Salimans", "Alexey Gritsenko", "William Chan", "Mohammad Norouzi", "David J Fleet"],
                                "year": 2022,
                                "conference": "",
                                "journal": "",
                                "url": "arXiv:2204.03458",
                                "doi": ""
                            },
                            "key_method_technology": "提出视频扩散模型并使用插补和类似无分类器引导机制适应输入帧条件",
                            "performance_improvement": "使视频模型能够基于输入帧进行条件生成",
                            "limitation": "未明确提及局限性"
                        }
                    ]
                },
                {
                    "class_name": "视频插值基准相关方法",
                    "class_description": "与视频插值基准相关的方法，用于推动视频插值器的发展，但通常基于线性或明确运动假设。",
                    "related_work_items": [
                        {
                            "article_info": {
                                "title": "A database and evaluation methodology for optical flow",
                                "authors": ["S. Baker", "D. Scharstein", "J.P. Lewis", "S. Roth", "M. J. Black", "R. Szeliski"],
                                "year": 2007,
                                "conference": "ICCV",
                                "journal": "",
                                "url": "",
                                "doi": ""
                            },
                            "key_method_technology": "提出光流数据库和评估方法",
                            "performance_improvement": "为光流和视频插值研究提供评估基础",
                            "limitation": "基于线性或明确运动假设，难以处理复杂运动"
                        },
                        {
                            "article_info": {
                                "title": "The 2017 davis challenge on video object segmentation",
                                "authors": ["Jordi Pont-Tuset", "Federico Perazzi", "Sergi Caelles", "Pablo Arbeláez", "Alex Sorkine-Hornung", "Luc Van Gool"],
                                "year": 2017,
                                "conference": "",
                                "journal": "",
                                "url": "arXiv preprint arXiv:1704.00675",
                                "doi": ""
                            },
                            "key_method_technology": "举办视频对象分割挑战，提供相关数据集",
                            "performance_improvement": "促进视频相关研究发展",
                            "limitation": "基于线性或明确运动假设，难以处理复杂运动"
                        }
                    ]
                }
            ]
        }
    }  
    
    ....
]
```


### 2. 论文引言和相关工作撰写
 - 用户输入想要撰写的论文题目或想要撰写论文的关键词，智能体会根据题目或关键词进行论文的引言和相关工作撰写。
 - 用户可以利用[功能1](#1-论文批量检索和知识提取)
 - 用户可自定义摘要和引言的字数(默认是摘要1000字，引言2000字)，任务运行时长与字数成正相

