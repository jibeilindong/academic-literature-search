# 学术文献检索技能

一个专注于文献检索的OpenClaw技能，提供快速、准确、全面的学术文献检索服务。

## 功能特性

- **多数据库集成**: Semantic Scholar, Crossref, PubMed, arXiv
- **高级检索**: 布尔搜索、字段限定、范围搜索
- **智能处理**: 去重、排序、过滤、结果丰富
- **多格式输出**: Markdown, JSON, CSV, BibTeX, RIS, Excel
- **性能优化**: 并发检索、智能缓存、渐进式加载

## 安装

### 方法一：通过OpenClaw安装
 bash 
openclaw skill install academic-literature-search

### 方法二：手动安装
1. 克隆仓库：
git clone https://github.com/openclaw/skills/academic-literature-search.git

2. 安装依赖：
cd academic-literature-search

pip install -r requirements.txt
bash
3. 配置环境变量：
Semantic Scholar API密钥（可选但推荐）

export SEMANTIC_SCHOLAR_API_KEY="your_email@example.com"

Crossref API邮箱（推荐）

export CROSSREF_API_EMAIL="your_email@example.com"

PubMed API密钥（可选）

export PUBMED_API_KEY="your_api_key"

4. 复制配置文件：
cp config.example.yaml config.yaml
编辑 config.yaml 配置

## 使用方法

### 基本用法

简单检索

openclaw literature-search "deep learning in medical imaging"

高级检索

openclaw literature-search \

--query "attention mechanism AND transformer" \

--databases semantic_scholar crossref \

--year-range 2020-2024 \

--max-results 100 \

--sort-by citations \

--open-access-only \

--output-format markdown \

--output-file results.md
### Python API


from literature_search import AcademicLiteratureSearchSkill

初始化技能

skill = AcademicLiteratureSearchSkill()

执行检索

params = {

"query": "large language models in healthcare",

"databases": ["semantic_scholar", "crossref"],

"max_results": 50,

"year_range": "2020-2024"

}

result = await skill.execute(params)

print(result["results"])


### 作为库使用

import asyncio

from literature_search import LiteratureSearchEngine

async def search():

async with LiteratureSearchEngine() as engine:

papers = await engine.search(

query="reinforcement learning",

databases=["semantic_scholar", "arxiv"],

max_results=20

)

for paper in papers:

print(f"{paper.title} - {paper.citation_count} citations")

asyncio.run(search())

## 参数说明

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| query | string | 必需 | 检索查询字符串 |
| databases | array | ["semantic_scholar", "crossref"] | 使用的数据库 |
| max_results | integer | 50 | 最大返回数量 |
| year_range | string | - | 年份范围，如 "2020-2024" |
| sort_by | string | "relevance" | 排序方式 |
| sort_order | string | "desc" | 排序顺序 |
| open_access_only | boolean | false | 仅开放获取 |
| min_citations | integer | - | 最小引用数 |
| output_format | string | "markdown" | 输出格式 |
| output_file | string | - | 输出文件路径 |
| interactive | boolean | false | 交互式模式 |
| cache | boolean | true | 启用缓存 |

## 输出格式

### Markdown示例

文献检索结果

检索词: deep learning in medical imaging

检索时间: 2024-01-15 14:30:00

结果数量: 20篇

检索结果

1. Deep Learning for Medical Image Analysis: A Comprehensive Review
作者: Geert Litjens, Thijs Kooi, Babak Ehteshami Bejnordi, et al.
出版信息: 2017年 | Medical Image Analysis
引用数: 4231
标识符: DOI: 10.1016/j.media.2017.07.005
摘要: Deep learning has emerged as a powerful tool...
访问: 原文链接| 🔓 开放获取

## 高级功能

### 1. 缓存系统
技能使用多级缓存系统：
- 内存缓存：5分钟TTL
- 磁盘缓存：1小时TTL
- 智能缓存键生成

### 2. 并发检索
- 并行查询多个数据库
- 智能请求调度
- 速率限制处理

### 3. 错误处理
- 自动重试机制
- 优雅降级
- 详细的错误信息


### 4. 性能监控
- 请求跟踪
- 响应时间统计
- 缓存命中率

## 配置

### 环境变量

bash

API密钥

SEMANTIC_SCHOLAR_API_KEY

CROSSREF_API_EMAIL

PUBMED_API_KEY

网络配置

HTTP_PROXY

HTTPS_PROXY

LITERATURE_SEARCH_TIMEOUT

缓存配置

LITERATURE_SEARCH_CACHE_ENABLED

LITERATURE_SEARCH_CACHE_DIR
复制
### 配置文件
编辑 `config.yaml`：
yaml

search:

default_max_results: 100

default_databases: ["semantic_scholar", "crossref", "pubmed"]

cache:

enabled: true

memory_cache_ttl: 600  # 10分钟

output:

default_format: "json"

auto_save: true
复制
## 故障排除

### 常见问题

1. **API速率限制**
   - 申请Semantic Scholar API密钥
   - 提供Crossref邮箱
   - 启用缓存减少请求

2. **网络问题**
   - 检查网络连接
   - 配置代理服务器
   - 增加超时时间

3. **无结果**
   - 检查查询语法
   - 尝试英文关键词
   - 扩大检索范围

### 调试模式
bash

export LITERATURE_SEARCH_LOG_LEVEL=DEBUG

openclaw literature-search "test query" --verbose
复制
## 开发

### 项目结构
academic-literature-search/

├── SKILL.md          # 技能描述

├── agent.py          # 主执行逻辑

├── skill.json        # 技能元信息

├── requirements.txt  # Python依赖

├── config.example.yaml  # 配置示例

├── tests/            # 测试文件

└── README.md         # 使用说明
复制
### 运行测试
bash

安装测试依赖

pip install pytest pytest-asyncio

运行测试

pytest tests/
复制
### 贡献指南
1. Fork仓库
2. 创建特性分支
3. 提交更改
4. 推送分支
5. 创建Pull Request

## 许可证
MIT License

## 支持
- 问题报告: [GitHub Issues](https://github.com/openclaw/skills/issues)
- 文档: [OpenClaw Docs](https://docs.openclaw.dev)
- 社区: [Discord](https://discord.gg/openclaw)
三、使用示例

1. 命令行使用
bash
复制
# 基本检索
openclaw literature-search "machine learning in healthcare"

# 带过滤的检索
openclaw literature-search \
  --query "transformer AND medical" \
  --year-range 2020-2024 \
  --min-citations 100 \
  --open-access-only

# 导出为JSON
openclaw literature-search \
  --query "reinforcement learning" \
  --output-format json \
  --output-file results.json

# 交互式模式
openclaw literature-search \
  --query "natural language processing" \
  --interactive
2. Python脚本使用
python
下载
复制
import asyncio
import json
from literature_search import AcademicLiteratureSearchSkill

async def main():
    # 初始化技能
    skill = AcademicLiteratureSearchSkill()
    
    # 定义检索参数
    params = {
        "query": "large language models in medical diagnosis",
        "databases": ["semantic_scholar", "crossref"],
        "max_results": 20,
        "year_range": "2020-2024",
        "sort_by": "citations",
        "open_access_only": True,
        "output_format": "markdown"
    }
    
    # 执行检索
    result = await skill.execute(params)
    
    if result["success"]:
        print(result["results"])
        print(f"\n检索到 {result['papers_count']} 篇文献")
    else:
        print(f"检索失败: {result['error']}")

# 运行
asyncio.run(main())
3. 作为库使用
python
下载
复制
import asyncio
from literature_search import LiteratureSearchEngine, OutputFormatter

async def advanced_search():
    async with LiteratureSearchEngine() as engine:
        # 并行检索多个数据库
        papers = await engine.search(
            query="(deep learning OR neural network) AND (medical OR healthcare)",
            databases=["semantic_scholar", "crossref", "pubmed"],
            max_results=50,
            year_range=(2018, 2024)
        )
        
        # 应用自定义过滤
        filtered_papers = [
            p for p in papers 
            if p.citation_count > 10 and p.is_open_access
        ]
        
        # 自定义排序
        filtered_papers.sort(key=lambda x: x.citation_count, reverse=True)
        
        # 格式化输出
        formatter = OutputFormatter()
        markdown_output = formatter.format_markdown(filtered_papers[:10])
        print(markdown_output)
        
        # 导出为BibTeX
        bibtex_output = formatter.format_bibtex(filtered_papers[:5])
        with open("references.bib", "w") as f:
            f.write(bibtex_output)

asyncio.run(advanced_search())

四、测试文件
tests/test_basic.py
python
下载
复制
#!/usr/bin/env python3
"""
基本测试
"""

import asyncio
import pytest
from unittest.mock import Mock, patch
from literature_search import AcademicLiteratureSearchSkill, Paper, Database

@pytest.mark.asyncio
async def test_basic_search():
    """测试基本检索"""
    skill = AcademicLiteratureSearchSkill()
    
    # 模拟参数
    params = {
        "query": "test query",
        "max_results": 5
    }
    
    # 模拟引擎返回
    with patch('literature_search.LiteratureSearchEngine') as mock_engine:
        mock_instance = Mock()
        mock_instance.search.return_value = [
            Paper(
                title="Test Paper 1",
                authors=["Author 1", "Author 2"],
                year=2023,
                venue="Test Conference",
                citation_count=10,
                doi="10.1234/test.1234"
            )
        ]
        mock_engine.return_value.__aenter__.return_value = mock_instance
        
        result = await skill.execute(params)
        
        assert result["success"] is True
        assert result["papers_count"] == 1
        assert "Test Paper 1" in result["results"]

@pytest.mark.asyncio
async def test_empty_query():
    """测试空查询"""
    skill = AcademicLiteratureSearchSkill()
    params = {"query": ""}
    
    result = await skill.execute(params)
    
    assert result["success"] is False
    assert "查询参数不能为空" in result["error"]

@pytest.mark.asyncio
async def test_invalid_database():
    """测试无效数据库"""
    skill = AcademicLiteratureSearchSkill()
    params = {
        "query": "test",
        "databases": ["invalid_db"]
    }
    
    result = await skill.execute(params)
    
    # 应该使用默认数据库
    assert result["success"] is True

def test_paper_dataclass():
    """测试Paper数据类"""
    paper = Paper(
        title="Test Title",
        authors=["Author 1", "Author 2"],
        year=2023,
        citation_count=100
    )
    
    assert paper.title == "Test Title"
    assert len(paper.authors) == 2
    assert paper.year == 2023
    assert paper.citation_count == 100
    
    # 测试转换为字典
    paper_dict = paper.to_dict()
    assert paper_dict["title"] == "Test Title"
    assert "authors" in paper_dict

if __name__ == "__main__":
    pytest.main([__file__, "-v"])
五、部署说明

1. 本地部署
bash
复制
# 克隆仓库
git clone https://github.com/openclaw/skills/academic-literature-search.git
cd academic-literature-search

# 安装依赖
pip install -r requirements.txt

# 配置环境变量
export SEMANTIC_SCHOLAR_API_KEY="your_email@example.com"
export CROSSREF_API_EMAIL="your_email@example.com"

# 测试
python -m pytest tests/
2. Docker部署
dockerfile
复制
FROM python:3.9-slim

WORKDIR /app

# 安装依赖
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 复制代码
COPY . .

# 设置环境变量
ENV PYTHONPATH=/app
ENV LITERATURE_SEARCH_CACHE_DIR=/cache

# 创建缓存目录
RUN mkdir -p /cache

# 运行测试
RUN python -m pytest tests/ -v

# 设置入口点
ENTRYPOINT ["python", "-m", "literature_search.agent"]
3. OpenClaw集成
bash
复制
# 安装到OpenClaw
openclaw skill install ./academic-literature-search

# 验证安装
openclaw skill list | grep literature-search

# 测试技能
openclaw skill test academic-literature-search \
  --params '{"query": "test query", "max_results": 5}'
六、性能优化建议

1. 缓存优化
使用Redis作为共享缓存
实现智能缓存预热
定期清理过期缓存
2. 并发优化
调整并发连接数
实现连接池
优化请求调度
3. 内存优化
使用生成器处理大量数据
实现分页加载
优化数据结构
4. 网络优化
使用HTTP/2
启用压缩
实现请求合并
总结

这个OpenClaw学术文献检索技能具有以下特点：
专注检索：专注于文献检索核心功能，不包含PDF解析、文献管理等辅助功能
功能强大：支持多数据库、高级查询、智能处理
性能优秀：并发检索、智能缓存、渐进式加载
易于使用：简洁的API、详细的文档、多种输出格式
可扩展：模块化设计、支持插件、易于定制
按照OpenClaw Skill核心结构整理后，这个技能可以：
直接被OpenClaw安装和使用
通过配置文件和环境变量灵活配置
支持命令行、Python API、库等多种使用方式
提供完整的文档和测试
易于维护和扩展
