# Enterprise Multi-Agent Business Intelligence Platform

Google Antigravity Enterprise BI Platform - A production-grade multi-agent workspace built on FastAPI, SQLAlchemy, ChromaDB, and LangGraph. It compiles natural language questions into query plans, generates secure SQL, aggregates analytical metrics, creates visualizations, predicts time-series forecasts, and exports downloadable PDF/Word/PPTX packages.

---

## Problem Statement

Business users need to query data using natural language without writing SQL. This platform implements a multi-agent system that understands questions, plans queries, executes them safely, and presents results as charts, forecasts, and reports.

## Objectives

- Natural language to SQL pipeline with security validation
- Multi-agent coordination for query planning, execution, analysis, visualization, forecasting
- Semantic data catalog for schema understanding
- Time-series forecasting with ARIMA and ML models
- Automated report generation (PDF/Word/PPTX)
- Enterprise-grade authentication and authorization

## Module Status Registry

| Module | Status | Key Classes |
|--------|--------|-------------|
| Authentication | ✅ Completed | `auth.py` |
| Database Connection Manager | ✅ Completed | `ConnectionService`, `connection_service.py` |
| Semantic Data Catalog | ✅ Completed | `CatalogService`, `catalog_service.py` |
| Query Planning Engine | ✅ Completed | `QueryPlannerService`, `query_planner.py` |
| SQL Generation & Optimizer | ✅ Completed | `SQLAgentService`, `sql_agent_service.py` |
| SQL Validation & Execution | ✅ Completed | `QueryExecutionService`, `query_execution_service.py` |
| Enterprise Analytics Agent | ✅ Completed | `AnalyticsService`, `analytics_service.py` |
| Enterprise Visualization Agent | ✅ Completed | `VisualizationService`, `visualization_service.py` |
| Enterprise Forecast Agent | ✅ Completed | `ForecastService`, `forecast_service.py` |
| Enterprise Recommendation Agent | ✅ Completed | `RecommendationService`, `recommendation_service.py` |
| Enterprise Report Agent | ✅ Completed | `ReportService`, `report_service.py` |
| LangGraph Multi-Agent Orchestrator | ✅ Completed | `OrchestratorService`, `orchestrator_service.py` |
| Enterprise RAG Knowledge Base | ✅ Completed | `RAGService`, `rag_service.py` |
| React 19 Frontend Web Client | ✅ Completed | `frontend/src/` |

## Technology Stack

| Layer | Technologies |
|-------|--------------|
| Backend | FastAPI, Python 3.12+, SQLAlchemy (Async), PostgreSQL/SQLite |
| Frontend | Next.js / Vite React 19, TypeScript, Tailwind CSS, Zustand, Recharts, Plotly |
| Vector Database | ChromaDB (Semantic Catalog, RAG Knowledge Base) |
| Multi-Agent Coordination | LangGraph StateGraph (Shared State routing) |
| Caching | Redis CacheManager |
| Forecasting Models | ARIMA & Lag-Feature Random Forest Regressor |

## Architecture

```
┌─────────────┐     ┌──────────────────┐     ┌─────────────────┐
│   Frontend  │────▶│   FastAPI API    │────▶│   PostgreSQL    │
│  (React 19) │     │  (Multi-Agent)   │     │   / SQLite      │
└─────────────┘     └────────┬─────────┘     └─────────────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        ┌──────────┐  ┌────────────┐  ┌──────────┐
        │ChromaDB  │  │   Redis    │  │  MLflow  │
        │(Catalog) │  │  (Cache)   │  │(Tracking)│
        └──────────┘  └────────────┘  └──────────┘
```

## Installation & Execution

### 1. Backend Application Setup
```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
```

### 2. Frontend Application Setup
```bash
cd frontend
npm install
npm run dev
```

### 3. Run Test Suite
```bash
.venv\Scripts\pytest.exe
```

## Key Capabilities

### Natural Language Querying
- User asks: "Show me monthly revenue by product category for 2024"
- System: Plans query → Generates secure SQL → Executes → Returns chart + data

### Semantic Data Catalog
- Automatic schema discovery
- Table/column descriptions
- Relationship mapping
- Embedding-based semantic search

### Multi-Agent Workflow
1. **Query Planner** - Decomposes question into steps
2. **SQL Agent** - Generates parameterized, validated SQL
3. **Execution Agent** - Runs query with safety limits
4. **Analytics Agent** - Computes aggregations, trends
5. **Visualization Agent** - Selects chart type, generates config
6. **Forecast Agent** - Runs ARIMA/ML models on time series
7. **Report Agent** - Packages results as PDF/Word/PPTX

### Forecasting
- ARIMA for classical time-series
- Random Forest with lag features for ML forecasting
- Model selection via backtesting
- Confidence intervals

### Security
- JWT authentication
- Role-based access control
- SQL injection prevention via parameterization
- Query execution timeouts and row limits

## Project Structure

```
enterprise-multi-agent-bi/
├── app/                    # FastAPI application
│   ├── main.py
│   ├── api/               # API routes
│   ├── services/          # Agent implementations
│   ├── models/            # Pydantic models
│   └── core/              # Config, security, database
├── frontend/              # React 19 + TypeScript
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── store/
│   └── package.json
├── docker-compose.yml
├── docker-compose.prod.yml
├── requirements.txt
├── Makefile
├── pytest.ini
├── deployment_guide.md
├── operations_manual.md
├── readiness_report.md
└── README.md
```

## Deployment

### Docker Compose (Development)
```bash
docker-compose up -d
```

### Production (Docker Compose)
```bash
docker-compose -f docker-compose.prod.yml up -d
```

### AWS ECS Fargate
See `deployment_guide.md` for CloudFormation template and setup.

## Monitoring

- Prometheus metrics at `/metrics`
- Grafana dashboards in `grafana/`
- Structured logging with correlation IDs
- Health checks at `/health`

---

## Author

**SAMALA RAKSHITH BABU**  

**Contact:**  
- Email: samalarakshithbabu7@gmail.com  
- LinkedIn: https://www.linkedin.com/in/samala-rakshith-babu/  
- GitHub: https://github.com/samalarakshithbabu  

---

## License

MIT License