# DEVELOPMENT_SLICES.md

> This document tracks development efforts by slice/month, showing what was planned, what was delivered, and what remains for future work.

## Development Approach

This project followed an iterative slice-based development approach where each month focused on a specific theme while building upon previous work.

1. Each slice built upon the previous one with increasing complexity
2. Core infrastructure work (Feb-Mar) enabled the semantic search capabilities (April)
3. Semantic search foundation (April) enabled the document QA features (May)
4. Document QA work (May) provided the basis for task engine development (June)
5. Task engine maturity (June) allowed for demo application development (July)
6. The MVP/demo application (July) unlocked extracting the core architecture for strategic pivot (August) as well as the deprecation of parts of the code-base.

The approach proved effective for managing complexity, though some features (like the task engine design) required more iteration than initially anticipated. Future slices will focus on stabilizing the architecture while adding new capabilities.

"Original Goals", "Targeted Deliverables", and "Scope Changes During Slice" declare the planned work while the "Actual Deliverables" are a list of ongoing or completed tasks. Completed tasks don't have to map to the declared deliverables and goals. If there is a mismatch between planned and actual deliverables, it is intentional to allow iterative planning and reflection.

## For Future Slices (Planned)

- Production Capabilities
- Complete permission model improvements
- Implement shared chat sessions
- Exportable conversation transcripts
- Model fine-tuning management
- MCP compatibility implementation
- Fix the openai model-provider implementation
- Implement a custom model gateway to allow elastic scaling

---

## August 2025 – Task Engine Refinement & Live Deployment

### Original Goals (Planned at Start)

- Refactor the engine to establish service boundaries
- Rewire existing frontends and bots
- Deploy a GitHub PR reviewer
- Documentation of the task engine spec
- Improve the modelprovider

### Targeted Deliverables (Planned Outcomes)

- Hook-Based Integration System: Migration to user-defined remote server connections
- GitHub Comment Synchronization: Fixing the "no way to compute a diff" issue
- Production-Ready PR Reviewer: Deploying a working GitHub PR review solution
- Task Engine Specification: Completing the documentation for chain definition and hook system
- Model Provider: Refactoring into a standalone reusable library

### Actual Deliverables (Completed Work)

- [x] Implement and test the new hook registry system for extensible integrations
- [x] Connection of existing hooks to the runtime via a bridge as a remote server connection
- [x] Generation of OpenAPI specification for the runtime via ast analysis
- [x] Automation of a initial CI and release process for the runtime
- [x] Refactor monorepo into multiple, dedicated libraries and service repositories
- [x] Add key API features: version endpoint, pagination, and simple authentication
- [x] Add API endpoints for exposing text embeddings
- [x] Create and integrate a new Go SDK for service-to-service communication
- [x] Improve model management to remove the hardcoded capabilities
- [x] Address breaking changes from Ollama-APIs and model behavior
- [x] Exanding E2E and compatibility testing
- [x] Improving the llmrepo and model provider management
- [x] ~~Fix UX and UI integration issues~~ (*Deprecated*)
- [x] Improving the llmresolver and fixing the engine to use the correct model
- [x] Implementing a new Request Response system via pubsub
- [x] Developing scripts for release automation and proper versioning
- [x] Fixing runtimestate hitting ratelimits of managed models
- [x] Implement a new chat service with dedicated API endpoints
- [x] Add OpenAI SSE (Server-Sent Events) support for streaming responses
- [x] Create a developer playground script for easier testing and environment setup
- [x] ~~Develop a Proof-of-Concept for a DSL visualizer in the legacy MVP frontend~~ (*Deprecated*)
- [x] Integrate & test open Web-UI as chat-client interface for the OpenAI completion endpoints

### Scope Changes During Slice

- **Added**: Token billing
- **Added**: Prepwork for the DSL-UI-Builder
- **Added**: Bot & Frontend configuration instead of Forms
- **Added**: Human-in-the-loop for the PR-reviewer

### Dependencies for Next Slice
- Task engine refactoring must be completed before major new features can be added
- Permission model improvements needed for multi-user collaboration features

## Effort Estimation
- 190 and 230 hours
- Core Refactoring: Migrating the entire engine from the monorepo.
- New Repository Setup: Establishing the CI/CD, testing, and release automation for the new runtime repository from scratch.
- Project Pivot: From all inclusive App to drop-in runtime.
- Legacy Code Maintenance: Simultaneously adapting the old mvp repository to work with the new, external engine.

## Unmet Goals
- Deploy a GitHub PR reviewer: The strategic pivot to a standalone runtime engine deprioritized the deployment of specific, application-level features.

---

## July 2025 – Building a demo application

### Original Goals (Planned at Start)

- ~~Package a persona-chat application~~
- ~~Implement basic observability and UI dashboard~~ (*Deprecated*)
- ~~Add API rate limiting middleware~~ (*Deprecated*)
- Implement chat moderation capabilites
- ~~Complete GitHub PR moderator functionality~~ (*Deprecated*)
- Fix task-engine design issues
- Improve permission model
- ~~Support multiple Telegram frontends via UI~~ (*Deprecated*)

### Targeted Deliverables (Planned Outcomes)

- Task Engine Enhancements: Improved system instruction handling and variable composition
- Activity Logging: Delivery of tracking and visualization of system activity
- ~~GitHub Integration: Delivery of PR tracking functionality and initial frontend~~ (*Deprecated*)
- ~~Bot Routing Improvements: Enhanced routing logic for bot commands~~ (*Deprecated*)
- Documentation Updates: Comprehensive documentation refresh to match current direction
- Tokenizer Fixes: Addressing tokenizer interface issues

### Actual Deliverables (Completed Work)

- [x] Basic Observability Integration
- [x] ~~UI Observability Dashboard~~ (*Deprecated*)
- [x] ~~API Rate Limiting Middleware~~ (*Deprecated*)
- [x] Implement Chat Moderation
- [x] ~~Declare multiple Telegram frontends via UI~~ (*Deprecated*)
- [x] ~~Activity tracking view improvements~~ (*Deprecated*)
- [x] Token count bug fixes
- [x] ~~Keyword extraction feature~~ (*Deprecated*)
- [x] ~~GitHub PR Moderator (core functionality complete but needs final polish)~~ (*Deprecated*)
- [x] Fix Task-Engine design (refactoring planned for next slice)
- [x] Add variable composition enhancements
- [x] ~~Integrated githubworker for PR handling~~ (*Deprecated*)
- [x] Fix the ollama model-provider implementation

### Scope Changes During Slice

- **Added**: Activity tracking view improvements
- **Added**: Token count bug fixes
- **Added**: Keyword extraction feature
- **Added**: Add variable composition enhancements

### Unmet Original Goals
- Package a Persona-Chat Application
- Permission Model Improvements (partially implemented)

### Effort Estimate
- 180-220 hours
- Focused on completing demo application with GitHub integration as the flagship feature

### Dependencies for Next Slice
- Task engine refactoring must be completed before major new features can be added
- Permission model improvements needed for multi-user collaboration features

---

## June 2025 – Taskengine & core

### Original Goals (Planned at Start)

- ~~Package a chat application with persona support~~ (*Deprecated*)
- ~~Add user registration~~ (*Deprecated*)
- Implement task execution commands
- Begin observability and release infrastructure

### Targeted Deliverables (Planned Outcomes)

- ~~RAG Implementation: Completed document retrieval and integration with LLM responses~~ (*Deprecated*)
- OpenAI-Compatible API: Added endpoints compatible with OpenAI's API format
- ~~Telegram Integration: Initial Telegram bot implementation with job queue system~~ (*Deprecated*)
- Gemini Integration: MVP implementation of Google Gemini provider
- vLLM Integration: Added support for vLLM inference server
- Testing Infrastructure: Comprehensive test suite for core components

### Actual Deliverables (Completed Work)

- [x] ~~RAG-Enhanced Chat Interface~~ (*Deprecated*)
- [x] Chat with Task Command Execution Support
- [x] Registration Route for Persona Chat Users
- [x] OpenAI Driver Integration
- [x] Gemini Driver Integration
- [x] Release Infrastructure Setup
- [x] ~~Telegram Bot Integrations~~ (*Deprecated*)
- [x] Simple OpenAI SDK-Compatible Chat Endpoint
- [x] vLLM Integration
- [x] Persisting Tasks
- [x] ~~Integration tests for dispatcher~~ (*Deprecated*)
- [x] ~~Worker authentication fixes~~ (*Deprecated*)
- [x] ~~Redesigned broker-worker architecture for improved async job handling~~ (*Deprecated*)
- [x] Prepare modelprovider to become a reusable library

### Scope Changes During Slice

- **Added**: None
- **Removed**: Formal release processes (deferred to re-architecture phase)

### Unmet Original Goals
- Packaging the platform as an application for persona-based chat (moved to next cycle)

### Effort Estimate
- 180-220 hours
- Focused on stabilizing core task execution framework and adding key integrations

---

## May 2025 – Documents QA

### Original Goals (Planned at Start)

- ~~Build a UI page for natural language document Q&A~~ (*Deprecated*)
- Prepare infrastructure for reusable prompt chains

### Targeted Deliverables (Planned Outcomes)

- ~~Job System: Implemented job queue system for processing background tasks~~ (*Deprecated*)
- ~~Files UI: Basic document management interface~~ (*Deprecated*)
- ~~Worker Infrastructure: Docker-compose integration for worker services~~ (*Deprecated*)
- Slice Planning Framework: Formalized development slice tracking system
- Task Engine Foundation: Initial implementation of the task execution framework
- Testing Improvements: Enhanced test coverage for document processing

### Actual Deliverables (Completed Work)

- [x] ~~Documents QA UI Page: Allows users to ask questions and get answers based on relevant documents~~ (*Deprecated*)
- [x] Prompt Execution Service: Executes prompts used by workers to chunk text
- [x] Prompt Chain Service: Runs sequences of prompts for QA and automation workflows
- [x] ~~Filesystem Performance Improvements: Optimized slow file operations~~ (*Deprecated*)
- [x] OpenAPI Spec Review: Reviewed endpoints and began planning documentation
- [x] Cleaning & Wiring: Ensured components were integrated and passing tests
- [x] ~~Python worker integration for document processing~~ (*Deprecated*)
- [x] ~~Resource type implementation for chunks~~ (*Deprecated*)
- [x] First implementation of the task engine
- [x] ~~Job cleanup logic implementation to prevent resource leaks~~ (*Deprecated*)

### Scope Changes During Slice

- **Added**: None
- **Removed**: None

### Unmet Original Goals

- None

### Effort Estimate
- 150-180 hours
- Focused on document processing pipeline and foundational task execution

---

## April 2025 – Semantic Search

### Original Goals (Planned at Start)

- ~~Enable semantic search over embedded documents~~ (*Deprecated*)
- Improve backend pooling and model routing logic
- Migrate tokenizer into a standalone service
- ~~Replace OpenSearch with Vald for vector search~~ (*Deprecated*)

### Targeted Deliverables (Planned Outcomes)

- Core Project Foundation: Initial project setup with MVP backend and admin-ui
- CI Pipeline: Implemented Go core tests and basic continuous integration
- ~~Authentication System: JWT-based authentication with access control lists~~ (*Deprecated*)
- ~~Vector Store Integration: Vald vector database implementation replacing OpenSearch~~ (*Deprecated*)
- ~~Document Processing Pipeline: Initial document ingestion and indexing system~~ (*Deprecated*)
- Testing Infrastructure: Basic test framework for core components

### Actual Deliverables (Completed Work)

- [x] ~~UI-Search Page: Developed to demo semantic search functionality~~ (*Deprecated*)
- [x] Backend Pooling: Finalized implementation of backend pools/fleets
- [x] Tokenizer Service Migration: Tokenizer logic moved to its own microservice
- [x] ~~Document Ingestion Pipeline:~~
- ~~Python workers now parse and process documents from the filestore~~
- ~~Embeddings are generated and ingested into Vald~~
- ~~Replaced OpenSearch with Vald for better gRPC support and Go integration~~ (*Deprecated*)
- [x] LLM Resolver Enhancements:
- Improved scoring system for selecting optimal backend/model
- Routing policies now consider load, capabilities, and availability
- [x] Fix wiring: Ensured previously built components worked end-to-end
- [x] Testing & CI: Fixed failing tests and set up basic Continuous Integration
- [x] ~~Authentication layer implementation~~ (*Deprecated*)
- [x] Activity tracking framework foundation
- [x] ~~Queue item leasing implementation for job reliability~~ (*Deprecated*)

### Scope Changes During Slice

- **Added**: None
- **Removed**: None

### Unmet Original Goals

### Effort Estimate
- 120-160 hours
- Focused on vector search implementation and core infrastructure

---

## February-March 2025 – Project Initialization

### Original Goals (Planned at Start)

- Establish foundational project structure
- Set up development environment for multi-language codebase
- Begin dependency management for cross-service communication

### Targeted Deliverables (Planned Outcomes)

- Project Scaffold: Initial directory structure and dependency management
- Core Tech Stack Setup: Go module initialization, Dockerfile templates
- Basic CI/CD Configuration: Minimal GitHub Actions workflow for testing
- Core Backend Implementation: Initial Go-based server architecture
- Database Integration: PostgreSQL setup and basic schema

### Actual Deliverables (Completed Work)

- [x] Multi-language Project Template (Go/Python/JS)
- [x] Dockerfile Base Templates
- [x] Initial GitHub Actions Workflow
- [x] Basic Makefile Targets
- [x] Directory Structure Convention
- [x] Core Go Server Implementation
- [x] PostgreSQL Integration
- [x] Initial Task Engine Prototype
- [x] ~~React Admin UI Skeleton~~ (*Deprecated*)
- [x] Enhanced CI/CD Pipeline
- [x] LLM API Routing Framework
- [x] ~~Basic Authentication System~~ (*Deprecated*)
- [x] ~~Initial File Storage System~~ (*Deprecated*)
- [x] Pub/Sub implementation for event-driven communication
- [x] Task engine skeleton implementation
- [x] Health checks for backend services and initial infrastructure setup
- [x] Developing the core for model syncing across distributed instances
- [x] Implementing a Circuit breaker and go routine manager library

### Scope Changes During Slice

- **Added**: None
- **Removed**: None

### Unmet Original Goals

- None

### Effort Estimate
- 140-180 hours
- Focused on establishing the core architecture and basic functionality

---
