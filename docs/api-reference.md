# API Reference

<div align="center">

![API Reference](https://img.shields.io/badge/📚_API_REFERENCE-Complete_Documentation-00FFFF?style=for-the-badge&labelColor=0A0A0A&color=00FFFF)

**Comprehensive API documentation for the Tiation ecosystem**

*Professional • Scalable • Mission-Driven*

[![🌐_Live_Demo](https://img.shields.io/badge/🌐_Live_Demo-tiation.github.io-00FFFF?style=flat-square&labelColor=0A0A0A)](https://tiation.github.io)
[![🔗_GitHub](https://img.shields.io/badge/🔗_GitHub-tiation-007FFF?style=flat-square&labelColor=0A0A0A)](https://github.com/tiation)
[![⚡_Status](https://img.shields.io/badge/⚡_Status-Active_Development-FF00FF?style=flat-square&labelColor=0A0A0A)](https://github.com/tiation/tiation.github.io)

</div>

---

## 🎯 Overview

This API reference provides comprehensive documentation for all Tiation ecosystem projects, including RESTful APIs, SDKs, CLI tools, and integration endpoints.

## 📋 Table of Contents

- [🤖 AI Agents API](#ai-agents)
- [📝 CMS API](#cms)
- [⚡ Terminal Workflows API](#terminal-workflows)
- [🐳 Docker Debian API](#docker-debian)
- [🏗️ Infrastructure API](#infrastructure)
- [🎲 Gaming APIs](#gaming-apis)
- [🌍 Social Impact APIs](#social-impact-apis)
- [🔧 Developer Tools APIs](#developer-tools-apis)
- [🔐 Authentication](#authentication)
- [📊 Rate Limiting](#rate-limiting)
- [🛠️ SDKs](#sdks)

---

## 🤖 AI Agents {#ai-agents}

### Base URL
```
https://api.tiation.ai/v1/agents
```

### Authentication
```bash
Authorization: Bearer YOUR_API_TOKEN
```

### Endpoints

#### Create Agent
```http
POST /agents
```

**Request Body:**
```json
{
  "name": "Customer Support Agent",
  "type": "conversational",
  "capabilities": ["nlp", "sentiment_analysis", "task_automation"],
  "model": "tiation-llm-v2",
  "config": {
    "temperature": 0.7,
    "max_tokens": 2048,
    "context_window": 8192
  }
}
```

**Response:**
```json
{
  "id": "agent_abc123",
  "name": "Customer Support Agent",
  "status": "active",
  "created_at": "2024-07-18T16:37:20Z",
  "endpoint": "https://api.tiation.ai/v1/agents/agent_abc123"
}
```

#### List Agents
```http
GET /agents
```

**Parameters:**
- `page` (optional): Page number (default: 1)
- `limit` (optional): Items per page (default: 20, max: 100)
- `type` (optional): Filter by agent type
- `status` (optional): Filter by status (active, inactive, training)

**Response:**
```json
{
  "agents": [
    {
      "id": "agent_abc123",
      "name": "Customer Support Agent",
      "type": "conversational",
      "status": "active",
      "created_at": "2024-07-18T16:37:20Z"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 1,
    "pages": 1
  }
}
```

#### Chat with Agent
```http
POST /agents/{agent_id}/chat
```

**Request Body:**
```json
{
  "message": "Hello, I need help with my account",
  "context": {
    "user_id": "user_xyz789",
    "session_id": "session_456"
  }
}
```

**Response:**
```json
{
  "response": "Hello! I'd be happy to help you with your account. What specific issue are you experiencing?",
  "confidence": 0.95,
  "tokens_used": 45,
  "session_id": "session_456",
  "timestamp": "2024-07-18T16:37:20Z"
}
```

---

## 📝 CMS {#cms}

### Base URL
```
https://api.tiation.cms/v1
```

### Endpoints

#### Content Management

**Create Content**
```http
POST /content
```

**Request Body:**
```json
{
  "title": "Getting Started with Tiation",
  "type": "article",
  "content": "# Welcome to Tiation\n\nThis is your introduction...",
  "tags": ["tutorial", "getting-started"],
  "author": "tiation-team",
  "status": "published"
}
```

**Get Content**
```http
GET /content/{content_id}
```

**Update Content**
```http
PUT /content/{content_id}
```

**Delete Content**
```http
DELETE /content/{content_id}
```

#### Media Management

**Upload Media**
```http
POST /media
```

**Get Media**
```http
GET /media/{media_id}
```

---

## ⚡ Terminal Workflows {#terminal-workflows}

### CLI Commands

#### Installation
```bash
npm install -g @tiation/terminal-workflows
```

#### Available Commands

**Initialize Workflow**
```bash
tiation-workflow init [workflow-name]
```

**List Workflows**
```bash
tiation-workflow list
```

**Run Workflow**
```bash
tiation-workflow run [workflow-name] [options]
```

**Create Custom Workflow**
```bash
tiation-workflow create [workflow-name] --template [template-type]
```

### Configuration

**Workflow Configuration File** (`tiation-workflow.json`):
```json
{
  "name": "deploy-production",
  "description": "Deploy application to production environment",
  "steps": [
    {
      "name": "run-tests",
      "command": "npm test",
      "condition": "always"
    },
    {
      "name": "build-app",
      "command": "npm run build",
      "condition": "success"
    },
    {
      "name": "deploy",
      "command": "kubectl apply -f deployment.yaml",
      "condition": "success"
    }
  ],
  "environment": {
    "NODE_ENV": "production",
    "API_URL": "https://api.tiation.ai"
  }
}
```

---

## 🐳 Docker Debian {#docker-debian}

### Docker Images

#### Base Images

**Tiation Base**
```dockerfile
FROM tiation/debian-base:latest
```

**Tiation Node.js**
```dockerfile
FROM tiation/node:18-debian
```

**Tiation Python**
```dockerfile
FROM tiation/python:3.11-debian
```

**Tiation Go**
```dockerfile
FROM tiation/go:1.21-debian
```

#### Enterprise Features

**Security Scanning**
```bash
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock \
  tiation/security-scanner:latest scan [image-name]
```

**Performance Monitoring**
```bash
docker run -d --name tiation-monitor \
  -p 3000:3000 \
  tiation/performance-monitor:latest
```

### Container Management API

#### Base URL
```
https://api.tiation.docker/v1
```

#### Endpoints

**List Containers**
```http
GET /containers
```

**Create Container**
```http
POST /containers
```

**Container Status**
```http
GET /containers/{container_id}/status
```

---

## 🏗️ Infrastructure {#infrastructure}

### Kubernetes Resources

#### Deployment Templates

**Tiation Application Deployment**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: tiation-app
  labels:
    app: tiation
    tier: frontend
spec:
  replicas: 3
  selector:
    matchLabels:
      app: tiation
      tier: frontend
  template:
    metadata:
      labels:
        app: tiation
        tier: frontend
    spec:
      containers:
      - name: tiation-app
        image: tiation/app:latest
        ports:
        - containerPort: 3000
        env:
        - name: NODE_ENV
          value: "production"
        - name: API_URL
          value: "https://api.tiation.ai"
```

#### Service Configuration

**Load Balancer Service**
```yaml
apiVersion: v1
kind: Service
metadata:
  name: tiation-service
spec:
  selector:
    app: tiation
    tier: frontend
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
  type: LoadBalancer
```

### Infrastructure API

#### Base URL
```
https://api.tiation.infra/v1
```

#### Endpoints

**Deploy Application**
```http
POST /deployments
```

**Get Deployment Status**
```http
GET /deployments/{deployment_id}
```

**Scale Application**
```http
PUT /deployments/{deployment_id}/scale
```

---

## 🎲 Gaming APIs {#gaming-apis}

### Dice Roller API

#### Base URL
```
https://api.tiation.gaming/v1/dice
```

#### Endpoints

**Roll Dice**
```http
POST /roll
```

**Request Body:**
```json
{
  "dice": "2d20+5",
  "advantage": false,
  "modifier": 0
}
```

**Response:**
```json
{
  "result": 25,
  "rolls": [12, 8],
  "modifier": 5,
  "formula": "2d20+5",
  "breakdown": "12 + 8 + 5 = 25"
}
```

### Shattered Realms API

#### Base URL
```
https://api.shattered-realms.com/v1
```

#### Character Management

**Create Character**
```http
POST /characters
```

**Get Character**
```http
GET /characters/{character_id}
```

---

## 🌍 Social Impact APIs {#social-impact-apis}

### Chase White Rabbit NGO API

#### Base URL
```
https://api.chasewhiterabbit.org/v1
```

#### Endpoints

**Submit Impact Report**
```http
POST /reports
```

**Get Impact Metrics**
```http
GET /metrics
```

### Protect Children Australia API

#### Base URL
```
https://api.protectchildren.au/v1
```

#### Endpoints

**Report Incident**
```http
POST /incidents
```

**Get Resources**
```http
GET /resources
```

---

## 🔧 Developer Tools APIs {#developer-tools-apis}

### Go SDK

#### Installation
```bash
go get github.com/tiation/tiation-go-sdk
```

#### Usage
```go
package main

import (
    "github.com/tiation/tiation-go-sdk/client"
    "github.com/tiation/tiation-go-sdk/agents"
)

func main() {
    client := client.New("your-api-key")
    agentClient := agents.New(client)
    
    agent, err := agentClient.Create(agents.CreateRequest{
        Name: "My Agent",
        Type: "conversational",
    })
    if err != nil {
        log.Fatal(err)
    }
    
    fmt.Printf("Created agent: %s\n", agent.ID)
}
```

### React Template

#### Installation
```bash
npx create-react-app my-app --template @tiation/react-template
```

#### Features
- Dark neon theme
- Tiation component library
- Pre-configured routing
- API integration helpers
- Testing setup

---

## 🔐 Authentication

### API Keys

All Tiation APIs use API key authentication:

```bash
Authorization: Bearer YOUR_API_TOKEN
```

### OAuth 2.0

For user-facing applications:

```bash
Authorization: Bearer YOUR_OAUTH_TOKEN
```

### Rate Limiting

- **Free Tier**: 1,000 requests/hour
- **Pro Tier**: 10,000 requests/hour
- **Enterprise**: Custom limits

### Error Responses

```json
{
  "error": {
    "code": "AUTHENTICATION_FAILED",
    "message": "Invalid API key provided",
    "details": "The API key is either missing or invalid"
  }
}
```

---

## 📊 Rate Limiting {#rate-limiting}

### Headers

All API responses include rate limit headers:

```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 995
X-RateLimit-Reset: 1642684800
```

### Rate Limit Exceeded

```json
{
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "Rate limit exceeded",
    "retry_after": 3600
  }
}
```

---

## 🛠️ SDKs {#sdks}

### Available SDKs

- **JavaScript/TypeScript**: `@tiation/sdk-js`
- **Python**: `tiation-sdk-python`
- **Go**: `tiation-go-sdk`
- **Java**: `tiation-sdk-java`
- **C#**: `Tiation.SDK`
- **Ruby**: `tiation-sdk-ruby`
- **PHP**: `tiation/sdk-php`

### Installation Examples

**JavaScript/TypeScript**
```bash
npm install @tiation/sdk-js
```

**Python**
```bash
pip install tiation-sdk-python
```

**Go**
```bash
go get github.com/tiation/tiation-go-sdk
```

### Usage Examples

**JavaScript**
```javascript
import { TiationClient } from '@tiation/sdk-js';

const client = new TiationClient('your-api-key');

const agent = await client.agents.create({
  name: 'My Agent',
  type: 'conversational'
});
```

**Python**
```python
from tiation import TiationClient

client = TiationClient('your-api-key')

agent = client.agents.create(
    name='My Agent',
    type='conversational'
)
```

---

## 🤝 Support

### Getting Help

- **Documentation**: This API reference
- **GitHub Issues**: [github.com/tiation/tiation/issues](https://github.com/tiation/tiation/issues)
- **Email**: tiatheone@protonmail.com
- **Community**: Join our Discord server

### Status Page

Monitor API status at: [status.tiation.ai](https://status.tiation.ai)

---

## 🔮 Tiation Ecosystem

This API reference is part of the Tiation ecosystem. Explore related projects:

- [🌟 TiaAstor](https://github.com/TiaAstor/TiaAstor) - Personal brand and story
- [🐰 ChaseWhiteRabbit NGO](https://github.com/tiation/tiation-chase-white-rabbit-ngo) - Social impact initiatives
- [🏗️ Infrastructure](https://github.com/tiation/tiation-rigger-infrastructure) - Enterprise infrastructure
- [🤖 AI Agents](https://github.com/tiation/tiation-ai-agents) - Intelligent automation
- [📝 CMS](https://github.com/tiation/tiation-cms) - Content management system
- [⚡ Terminal Workflows](https://github.com/tiation/tiation-terminal-workflows) - Developer tools

---

*Built with 💜 by the Tiation team*

<div align="center">

![Footer](https://img.shields.io/badge/🔮_TIATION_ECOSYSTEM-API_Reference-00FFFF?style=for-the-badge&labelColor=0A0A0A&color=00FFFF)

</div>
