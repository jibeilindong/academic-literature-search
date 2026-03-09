# \u5b66\u672f\u6587\u732e\u68c0\u7d22\u6280\u80fd

\u4e00\u4e2a\u4e13\u6ce8\u4e8e\u6587\u732e\u68c0\u7d22\u7684OpenClaw\u6280\u80fd\uff0c\u63d0\u4f9b\u5feb\u901f\u3001\u51c6\u786e\u3001\u5168\u9762\u7684\u5b66\u672f\u6587\u732e\u68c0\u7d22\u670d\u52a1\u3002

## \u529f\u80fd\u7279\u6027

- **\u591a\u6570\u636e\u5e93\u96c6\u6210**: Semantic Scholar, Crossref, PubMed, arXiv
- **\u9ad8\u7ea7\u68c0\u7d22**: \u5e03\u5c14\u641c\u7d22\u3001\u5b57\u6bb5\u9650\u5b9a\u3001\u8303\u56f4\u641c\u7d22
- **\u667a\u80fd\u5904\u7406**: \u53bb\u91cd\u3001\u6392\u5e8f\u3001\u8fc7\u6ee4\u3001\u7ed3\u679c\u4e30\u5bcc
- **\u591a\u683c\u5f0f\u8f93\u51fa**: Markdown, JSON, CSV, BibTeX, RIS, Excel
- **\u6027\u80fd\u4f18\u5316**: \u5e76\u53d1\u68c0\u7d22\u3001\u667a\u80fd\u7f13\u5b58\u3001\u6e10\u8fdb\u5f0f\u52a0\u8f7d

## \u5b89\u88c5

### \u65b9\u6cd5\u4e00\uff1a\u901a\u8fc7OpenClaw\u5b89\u88c5
openclaw skill install academic-literature-search

### \u65b9\u6cd5\u4e8c\uff1a\u624b\u52a8\u5b89\u88c5
1. \u514b\u9686\u4ed3\u5e93\uff1a
git clone https://github.com/openclaw/skills/academic-literature-search.git

2. \u5b89\u88c5\u4f9d\u8d56\uff1a
cd academic-literature-search

pip install -r requirements.txt

3. \u914d\u7f6e\u73af\u5883\u53d8\u91cf\uff1a
Semantic Scholar API\u5bc6\u94a5\uff08\u53ef\u9009\u4f46\u63a8\u8350\uff09

export SEMANTIC_SCHOLAR_API_KEY="your_email@example.com"

Crossref API\u90ae\u7bb1\uff08\u63a8\u8350\uff09

export CROSSREF_API_EMAIL="your_email@example.com"

PubMed API\u5bc6\u94a5\uff08\u53ef\u9009\uff09

export PUBMED_API_KEY="your_api_key"

4. \u590d\u5236\u914d\u7f6e\u6587\u4ef6\uff1a
cp config.example.yaml config.yaml
\u7f16\u8f91 config.yaml \u914d\u7f6e

## \u4f7f\u7528\u65b9\u6cd5

### \u57fa\u672c\u7528\u6cd5

\u7b80\u5355\u68c0\u7d22

openclaw literature-search "deep learning in medical imaging"

\u9ad8\u7ea7\u68c0\u7d22

openclaw literature-search \\

--query "attention mechanism AND transformer" \\

--databases semantic_scholar crossref \\

--year-range 2020-2024 \\

--max-results 100 \\

--sort-by citations \\

--open-access-only \\

--output-format markdown \\

--output-file results.md
### Python API


from literature_search import AcademicLiteratureSearchSkill

\u521d\u59cb\u5316\u6280\u80fd

skill = AcademicLiteratureSearchSkill()

\u6267\u884c\u68c0\u7d22

params = {

"query": "large language models in healthcare",

"databases": ["semantic_scholar", "crossref"],

"max_results": 50,

"year_range": "2020-2024"

}

result = await skill.execute(params)

print(result["results"])


### \u4f5c\u4e3a\u5e93\u4f7f\u7528

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

## \u53c2\u6570\u8bf4\u660e

| \u53c2\u6570 | \u7c7b\u578b | \u9ed8\u8ba4\u503c | \u8bf4\u660e |
|------|------|--------|------|
| query | string | \u5fc5\u9700 | \u68c0\u7d22\u67e5\u8be2\u5b57\u7b26\u4e32 |
| databases | array | ["semantic_scholar", "crossref"] | \u4f7f\u7528\u7684\u6570\u636e\u5e93 |
| max_results | integer | 50 | \u6700\u5927\u8fd4\u56de\u6570\u91cf |
| year_range | string | - | \u5e74\u4efd\u8303\u56f4\uff0c\u5982 "2020-2024" |
| sort_by | string | "relevance" | \u6392\u5e8f\u65b9\u5f0f |
| sort_order | string | "desc" | \u6392\u5e8f\u987a\u5e8f |
| open_access_only | boolean | false | \u4ec5\u5f00\u653e\u83b7\u53d6 |
| min_citations | integer | - | \u6700\u5c0f\u5f15\u7528\u6570 |
| output_format | string | "markdown" | \u8f93\u51fa\u683c\u5f0f |
| output_file | string | - | \u8f93\u51fa\u6587\u4ef6\u8def\u5f84 |
| interactive | boolean | false | \u4ea4\u4e92\u5f0f\u6a21\u5f0f |
| cache | boolean | true | \u542f\u7528\u7f13\u5b58 |

## \u8f93\u51fa\u683c\u5f0f

### Markdown\u793a\u4f8b

\u6587\u732e\u68c0\u7d22\u7ed3\u679c

\u68c0\u7d22\u8bcd: deep learning in medical imaging

\u68c0\u7d22\u65f6\u95f4: 2024-01-15 14:30:00

\u7ed3\u679c\u6570\u91cf: 20\u7bc7

\u68c0\u7d22\u7ed3\u679c

1. Deep Learning for Medical Image Analysis: A Comprehensive Review
\u4f5c\u8005: Geert Litjens, Thijs Kooi, Babak Ehteshami Bejnordi, et al.
\u51fa\u7248\u4fe1\u606f: 2017\u5e74 | Medical Image Analysis
\u5f15\u7528\u6570: 4231
\u6807\u8bc6\u7b26: DOI: 10.1016/j.media.2017.07.005
\u6458\u8981: Deep learning has emerged as a powerful tool...
\u8bbf\u95ee: \u539f\u6587\u94fe\u63a5| \ud83d\udd13 \u5f00\u653e\u83b7\u53d6

## \u9ad8\u7ea7\u529f\u80fd

### 1. \u7f13\u5b58\u7cfb\u7edf
\u6280\u80fd\u4f7f\u7528\u591a\u7ea7\u7f13\u5b58\u7cfb\u7edf\uff1a
- \u5185\u5b58\u7f13\u5b58\uff1a5\u5206\u949fTTL
- \u78c1\u76d8\u7f13\u5b58\uff1a1\u5c0f\u65f6TTL
- \u667a\u80fd\u7f13\u5b58\u952e\u751f\u6210

### 2. \u5e76\u53d1\u68c0\u7d22
- \u5e76\u884c\u67e5\u8be2\u591a\u4e2a\u6570\u636e\u5e93
- \u667a\u80fd\u8bf7\u6c42\u8c03\u5ea6
- \u901f\u7387\u9650\u5236\u5904\u7406

### 3. \u9519\u8bef\u5904\u7406
- \u81ea\u52a8\u91cd\u8bd5\u673a\u5236
- \u4f18\u96c5\u964d\u7ea7
- \u8be6\u7ec6\u7684\u9519\u8bef\u4fe1\u606f


### 4. \u6027\u80fd\u76d1\u63a7
- \u8bf7\u6c42\u8ddf\u8e2a
- \u54cd\u5e94\u65f6\u95f4\u7edf\u8ba1
- \u7f13\u5b58\u547d\u4e2d\u7387

## \u914d\u7f6e

### \u73af\u5883\u53d8\u91cf

bash

API\u5bc6\u94a5

SEMANTIC_SCHOLAR_API_KEY

CROSSREF_API_EMAIL

PUBMED_API_KEY

\u7f51\u7edc\u914d\u7f6e

HTTP_PROXY

HTTPS_PROXY

LITERATURE_SEARCH_TIMEOUT

\u7f13\u5b58\u914d\u7f6e

LITERATURE_SEARCH_CACHE_ENABLED

LITERATURE_SEARCH_CACHE_DIR
\u590d\u5236
### \u914d\u7f6e\u6587\u4ef6
\u7f16\u8f91 `config.yaml`\uff1a
yaml

search:

default_max_results: 100

default_databases: ["semantic_scholar", "crossref", "pubmed"]

cache:

enabled: true

memory_cache_ttl: 600  # 10\u5206\u949f

output:

default_format: "json"

auto_save: true
\u590d\u5236
## \u6545\u969c\u6392\u9664

### \u5e38\u89c1\u95ee\u9898

1. **API\u901f\u7387\u9650\u5236**
   - \u7533\u8bf7Semantic Scholar API\u5bc6\u94a5
   - \u63d0\u4f9bCrossref\u90ae\u7bb1
   - \u542f\u7528\u7f13\u5b58\u51cf\u5c11\u8bf7\u6c42

2. **\u7f51\u7edc\u95ee\u9898**
   - \u68c0\u67e5\u7f51\u7edc\u8fde\u63a5
   - \u914d\u7f6e\u4ee3\u7406\u670d\u52a1\u5668
   - \u589e\u52a0\u8d85\u65f6\u65f6\u95f4

3. **\u65e0\u7ed3\u679c**
   - \u68c0\u67e5\u67e5\u8be2\u8bed\u6cd5
   - \u5c1d\u8bd5\u82f1\u6587\u5173\u952e\u8bcd
   - \u6269\u5927\u68c0\u7d22\u8303\u56f4

### \u8c03\u8bd5\u6a21\u5f0f
bash

export LITERATURE_SEARCH_LOG_LEVEL=DEBUG

openclaw literature-search "test query" --verbose
\u590d\u5236
## \u5f00\u53d1

### \u9879\u76ee\u7ed3\u6784
academic-literature-search/

\u251c\u2500\u2500 SKILL.md          # \u6280\u80fd\u63cf\u8ff0

\u251c\u2500\u2500 agent.py          # \u4e3b\u6267\u884c\u903b\u8f91

\u251c\u2500\u2500 skill.json        # \u6280\u80fd\u5143\u4fe1\u606f

\u251c\u2500\u2500 requirements.txt  # Python\u4f9d\u8d56

\u251c\u2500\u2500 config.example.yaml  # \u914d\u7f6e\u793a\u4f8b

\u251c\u2500\u2500 tests/            # \u6d4b\u8bd5\u6587\u4ef6

\u2514\u2500\u2500 README.md         # \u4f7f\u7528\u8bf4\u660e
\u590d\u5236
### \u8fd0\u884c\u6d4b\u8bd5
bash

\u5b89\u88c5\u6d4b\u8bd5\u4f9d\u8d56

pip install pytest pytest-asyncio

\u8fd0\u884c\u6d4b\u8bd5

pytest tests/
\u590d\u5236
### \u8d21\u732e\u6307\u5357
1. Fork\u4ed3\u5e93
2. \u521b\u5efa\u7279\u6027\u5206\u652f
3. \u63d0\u4ea4\u66f4\u6539
4. \u63a8\u9001\u5206\u652f
5. \u521b\u5efaPull Request

## \u8bb8\u53ef\u8bc1
MIT License

## \u652f\u6301
- \u95ee\u9898\u62a5\u544a: [GitHub Issues](https://github.com/openclaw/skills/issues)
- \u6587\u6863: [OpenClaw Docs](https://docs.openclaw.dev)
- \u793e\u533a: [Discord](https://discord.gg/openclaw)
\u4e09\u3001\u4f7f\u7528\u793a\u4f8b

1. \u547d\u4ee4\u884c\u4f7f\u7528
bash
\u590d\u5236
# \u57fa\u672c\u68c0\u7d22
openclaw literature-search "machine learning in healthcare"

# \u5e26\u8fc7\u6ee4\u7684\u68c0\u7d22
openclaw literature-search \\
  --query "transformer AND medical" \\
  --year-range 2020-2024 \\
  --min-citations 100 \\
  --open-access-only

# \u5bfc\u51fa\u4e3aJSON
openclaw literature-search \\
  --query "reinforcement learning" \\
  --output-format json \\
  --output-file results.json

# \u4ea4\u4e92\u5f0f\u6a21\u5f0f
openclaw literature-search \\
  --query "natural language processing" \\
  --interactive
2. Python\u811a\u672c\u4f7f\u7528
python
\u4e0b\u8f7d
\u590d\u5236
import asyncio
import json
from literature_search import AcademicLiteratureSearchSkill

async def main():
    # \u521d\u59cb\u5316\u6280\u80fd
    skill = AcademicLiteratureSearchSkill()
    
    # \u5b9a\u4e49\u68c0\u7d22\u53c2\u6570
    params = {
        "query": "large language models in medical diagnosis",
        "databases": ["semantic_scholar", "crossref"],
        "max_results": 20,
        "year_range": "2020-2024",
        "sort_by": "citations",
        "open_access_only": True,
        "output_format": "markdown"
    }
    
    # \u6267\u884c\u68c0\u7d22
    result = await skill.execute(params)
    
    if result["success"]:
        print(result["results"])
        print(f"\\n\u68c0\u7d22\u5230 {result['papers_count']} \u7bc7\u6587\u732e")
    else:
        print(f"\u68c0\u7d22\u5931\u8d25: {result['error']}")

# \u8fd0\u884c
asyncio.run(main())
3. \u4f5c\u4e3a\u5e93\u4f7f\u7528
python
\u4e0b\u8f7d
\u590d\u5236
import asyncio
from literature_search import LiteratureSearchEngine, OutputFormatter

async def advanced_search():
    async with LiteratureSearchEngine() as engine:
        # \u5e76\u884c\u68c0\u7d22\u591a\u4e2a\u6570\u636e\u5e93
        papers = await engine.search(
            query="(deep learning OR neural network) AND (medical OR healthcare)",
            databases=["semantic_scholar", "crossref", "pubmed"],
            max_results=50,
            year_range=(2018, 2024)
        )
        
        # \u5e94\u7528\u81ea\u5b9a\u4e49\u8fc7\u6ee4
        filtered_papers = [
            p for p in papers 
            if p.citation_count > 10 and p.is_open_access
        ]
        
        # \u81ea\u5b9a\u4e49\u6392\u5e8f
        filtered_papers.sort(key=lambda x: x.citation_count, reverse=True)
        
        # \u683c\u5f0f\u5316\u8f93\u51fa
        formatter = OutputFormatter()
        markdown_output = formatter.format_markdown(filtered_papers[:10])
        print(markdown_output)
        
        # \u5bfc\u51fa\u4e3aBibTeX
        bibtex_output = formatter.format_bibtex(filtered_papers[:5])
        with open("references.bib", "w") as f:
            f.write(bibtex_output)

asyncio.run(advanced_search())
\u56db\u3001\u6d4b\u8bd5\u6587\u4ef6

tests/test_basic.py
python
\u4e0b\u8f7d
\u590d\u5236
#!/usr/bin/env python3
"""
\u57fa\u672c\u6d4b\u8bd5
"""

import asyncio
import pytest
from unittest.mock import Mock, patch
from literature_search import AcademicLiteratureSearchSkill, Paper, Database

@pytest.mark.asyncio
async def test_basic_search():
    """\u6d4b\u8bd5\u57fa\u672c\u68c0\u7d22"""
    skill = AcademicLiteratureSearchSkill()
    
    # \u6a21\u62df\u53c2\u6570
    params = {
        "query": "test query",
        "max_results": 5
    }
    
    # \u6a21\u62df\u5f15\u64ce\u8fd4\u56de
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
    """\u6d4b\u8bd5\u7a7a\u67e5\u8be2"""
    skill = AcademicLiteratureSearchSkill()
    params = {"query": ""}
    
    result = await skill.execute(params)
    
    assert result["success"] is False
    assert "\u67e5\u8be2\u53c2\u6570\u4e0d\u80fd\u4e3a\u7a7a" in result["error"]

@pytest.mark.asyncio
async def test_invalid_database():
    """\u6d4b\u8bd5\u65e0\u6548\u6570\u636e\u5e93"""
    skill = AcademicLiteratureSearchSkill()
    params = {
        "query": "test",
        "databases": ["invalid_db"]
    }
    
    result = await skill.execute(params)
    
    # \u5e94\u8be5\u4f7f\u7528\u9ed8\u8ba4\u6570\u636e\u5e93
    assert result["success"] is True

def test_paper_dataclass():
    """\u6d4b\u8bd5Paper\u6570\u636e\u7c7b"""
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
    
    # \u6d4b\u8bd5\u8f6c\u6362\u4e3a\u5b57\u5178
    paper_dict = paper.to_dict()
    assert paper_dict["title"] == "Test Title"
    assert "authors" in paper_dict

if __name__ == "__main__":
    pytest.main([__file__, "-v"])
\u4e94\u3001\u90e8\u7f72\u8bf4\u660e

1. \u672c\u5730\u90e8\u7f72
bash
\u590d\u5236
# \u514b\u9686\u4ed3\u5e93
git clone https://github.com/openclaw/skills/academic-literature-search.git
cd academic-literature-search

# \u5b89\u88c5\u4f9d\u8d56
pip install -r requirements.txt

# \u914d\u7f6e\u73af\u5883\u53d8\u91cf
export SEMANTIC_SCHOLAR_API_KEY="your_email@example.com"
export CROSSREF_API_EMAIL="your_email@example.com"

# \u6d4b\u8bd5
python -m pytest tests/
2. Docker\u90e8\u7f72
dockerfile
\u590d\u5236
FROM python:3.9-slim

WORKDIR /app

# \u5b89\u88c5\u4f9d\u8d56
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# \u590d\u5236\u4ee3\u7801
COPY . .

# \u8bbe\u7f6e\u73af\u5883\u53d8\u91cf
ENV PYTHONPATH=/app
ENV LITERATURE_SEARCH_CACHE_DIR=/cache

# \u521b\u5efa\u7f13\u5b58\u76ee\u5f55
RUN mkdir -p /cache

# \u8fd0\u884c\u6d4b\u8bd5
RUN python -m pytest tests/ -v

# \u8bbe\u7f6e\u5165\u53e3\u70b9
ENTRYPOINT ["python", "-m", "literature_search.agent"]
3. OpenClaw\u96c6\u6210
bash
\u590d\u5236
# \u5b89\u88c5\u5230OpenClaw
openclaw skill install ./academic-literature-search

# \u9a8c\u8bc1\u5b89\u88c5
openclaw skill list | grep literature-search

# \u6d4b\u8bd5\u6280\u80fd
openclaw skill test academic-literature-search \\
  --params '{"query": "test query", "max_results": 5}'
\u516d\u3001\u6027\u80fd\u4f18\u5316\u5efa\u8bae

1. \u7f13\u5b58\u4f18\u5316
\u4f7f\u7528Redis\u4f5c\u4e3a\u5171\u4eab\u7f13\u5b58
\u5b9e\u73b0\u667a\u80fd\u7f13\u5b58\u9884\u70ed
\u5b9a\u671f\u6e05\u7406\u8fc7\u671f\u7f13\u5b58
2. \u5e76\u53d1\u4f18\u5316
\u8c03\u6574\u5e76\u53d1\u8fde\u63a5\u6570
\u5b9e\u73b0\u8fde\u63a5\u6c60
\u4f18\u5316\u8bf7\u6c42\u8c03\u5ea6
3. \u5185\u5b58\u4f18\u5316
\u4f7f\u7528\u751f\u6210\u5668\u5904\u7406\u5927\u91cf\u6570\u636e
\u5b9e\u73b0\u5206\u9875\u52a0\u8f7d
\u4f18\u5316\u6570\u636e\u7ed3\u6784
4. \u7f51\u7edc\u4f18\u5316
\u4f7f\u7528HTTP/2
\u542f\u7528\u538b\u7f29
\u5b9e\u73b0\u8bf7\u6c42\u5408\u5e76
\u603b\u7ed3

\u8fd9\u4e2aOpenClaw\u5b66\u672f\u6587\u732e\u68c0\u7d22\u6280\u80fd\u5177\u6709\u4ee5\u4e0b\u7279\u70b9\uff1a
\u4e13\u6ce8\u68c0\u7d22\uff1a\u4e13\u6ce8\u4e8e\u6587\u732e\u68c0\u7d22\u6838\u5fc3\u529f\u80fd\uff0c\u4e0d\u5305\u542bPDF\u89e3\u6790\u3001\u6587\u732e\u7ba1\u7406\u7b49\u8f85\u52a9\u529f\u80fd
\u529f\u80fd\u5f3a\u5927\uff1a\u652f\u6301\u591a\u6570\u636e\u5e93\u3001\u9ad8\u7ea7\u67e5\u8be2\u3001\u667a\u80fd\u5904\u7406
\u6027\u80fd\u4f18\u79c0\uff1a\u5e76\u53d1\u68c0\u7d22\u3001\u667a\u80fd\u7f13\u5b58\u3001\u6e10\u8fdb\u5f0f\u52a0\u8f7d
\u6613\u4e8e\u4f7f\u7528\uff1a\u7b80\u6d01\u7684API\u3001\u8be6\u7ec6\u7684\u6587\u6863\u3001\u591a\u79cd\u8f93\u51fa\u683c\u5f0f
\u53ef\u6269\u5c55\uff1a\u6a21\u5757\u5316\u8bbe\u8ba1\u3001\u652f\u6301\u63d2\u4ef6\u3001\u6613\u4e8e\u5b9a\u5236
\u6309\u7167OpenClaw Skill\u6838\u5fc3\u7ed3\u6784\u6574\u7406\u540e\uff0c\u8fd9\u4e2a\u6280\u80fd\u53ef\u4ee5\uff1a
\u76f4\u63a5\u88abOpenClaw\u5b89\u88c5\u548c\u4f7f\u7528
\u901a\u8fc7\u914d\u7f6e\u6587\u4ef6\u548c\u73af\u5883\u53d8\u91cf\u7075\u6d3b\u914d\u7f6e
\u652f\u6301\u547d\u4ee4\u884c\u3001Python API\u3001\u5e93\u7b49\u591a\u79cd\u4f7f\u7528\u65b9\u5f0f
\u63d0\u4f9b\u5b8c\u6574\u7684\u6587\u6863\u548c\u6d4b\u8bd5
\u6613\u4e8e\u7ef4\u62a4\u548c\u6269\u5c55
