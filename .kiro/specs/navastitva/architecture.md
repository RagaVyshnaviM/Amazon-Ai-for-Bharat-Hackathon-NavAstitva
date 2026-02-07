# NavAstitva - AWS Reference Architecture

## Architecture Overview

This architecture is designed for:
- **Low bandwidth optimization** (rural 2G/3G connectivity)
- **Cost efficiency** (serverless-first approach)
- **Scalability** (handles millions of workers)
- **Multilingual support** (12+ Indian languages)

---

## Architecture Diagram

```
┌────────────────────────────────────────────────────────────────────┐
│                          CLIENT LAYER                              │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│  ┌──────────────┐         ┌──────────────┐      ┌──────────────┐   │
│  │   Flutter    │         │   Flutter    │      │  Enrollment  │   │
│  │  Mobile App  │         │   Web App    │      │    Kiosk     │   │
│  │  (Workers)   │         │(Employers/   │      │ (Panchayats) │   │
│  │              │         │  Clients)    │      │              │   │
│  └──────┬───────┘         └──────┬───────┘      └──────┬───────┘   │
│         │                        │                     │           │
│         └────────────────────────┼─────────────────────┘           │
│                                  │                                 │
└──────────────────────────────────┼─────────────────────────────────┘
                                   │
                                   │ HTTPS
                                   │
┌──────────────────────────────────▼──────────────────────────────────┐
│                         EDGE & CDN LAYER                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌────────────────────────────────────────────────────────────┐     │
│  │              Amazon CloudFront (CDN)                       │     │
│  │  • Caches static content & compressed videos               │     │
│  │  • Edge locations across India                             │     │
│  │  • Reduces bandwidth for repeat views                      │     │
│  └────────────────────────┬───────────────────────────────────┘     │
│                           │                                         │
└───────────────────────────┼─────────────────────────────────────────┘
                            │
┌───────────────────────────▼────────────────────────────────────────── ┐
│                      API GATEWAY LAYER                                │
├────────────────────────────────────────────────────────────────────── ┤
│                                                                       │
│  ┌──────────────────────────────────────────────────────────────┐     │
│  │              Amazon API Gateway (REST/WebSocket)             │     │
│  │  • Rate limiting & throttling                                │     │
│  │  • Request validation                                        │     │
│  │  • API key management                                        │     │
│  └────────────────┬─────────────────────────────────────────────┘     │
│                   │                                                   │
└───────────────────┼───────────────────────────────────────────────────┘
                    │
                    │
┌───────────────────▼───────────────────────────────────────────────────┐
│                    COMPUTE LAYER (Serverless)                         │
├───────────────────────────────────────────────────────────────────────┤
│                                                                       │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐   │
│  │   Lambda    │  │   Lambda    │  │   Lambda    │  │   Lambda    │   │
│  │   Worker    │  │  Employer/  │  │    Video    │  │   Payment   │   │
│  │  Services   │  │   Client    │  │  Processing │  │   Handler   │   │
│  │             │  │  Services   │  │             │  │             │   │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘   │
│         │                │                │                │          │
└─────────┼────────────────┼────────────────┼────────────────┼──────────┘
          │                │                │                │
          │                │                │                │
┌─────────▼────────────────▼────────────────▼────────────────▼──────────┐
│                         AI & ML LAYER                                 │
├───────────────────────────────────────────────────────────────────────┤
│                                                                       │
│  ┌──────────────────────────────────────────────────────────────┐     │
│  │                    Amazon Bedrock                            │     │
│  │  ┌────────────┐  ┌────────────┐  ┌────────────┐              │     │
│  │  │  Claude 3  │  │  Titan     │  │  Stable    │              │     │
│  │  │  (Text)    │  │ (Multimodal│  │  Diffusion │              │     │
│  │  │            │  │  Embeddings│  │  (Images)  │              │     │
│  │  └────────────┘  └────────────┘  └────────────┘              │     │
│  │                                                              │     │
│  │  • Skill verification from video                             │     │
│  │  • Multilingual translation (12+ languages)                  │     │
│  │  • Voice-to-text transcription                               │     │
│  │  • Fair wage recommendation                                  │     │
│  │  • Fraud detection                                           │     │
│  │  • Job & contract matching                                   │     │
│  └──────────────────────────────────────────────────────────────┘     │
│                                                                       │
│  ┌──────────────────────────────────────────────────────────────┐     │
│  │              Amazon Recognition                              │     │
│  │  • Video analysis (tool detection, safety protocols)         │     │
│  │  • Face verification (prevent video plagiarism)              │     │
│  │  • Content moderation                                        │     │
│  └──────────────────────────────────────────────────────────────┘     │
│                                                                       │
│  ┌──────────────────────────────────────────────────────────────┐     │
│  │              Amazon Transcribe                               │     │
│  │  • Voice-to-text (Hindi, Tamil, Telugu, Bengali, etc.)       │     │
│  │  • Custom vocabulary for trade-specific terms                │     │
│  └──────────────────────────────────────────────────────────────┘     │
│                                                                       │
│  ┌──────────────────────────────────────────────────────────────┐     │
│  │              Amazon Translate                                │     │
│  │  • Real-time language translation                            │     │
│  │  • Worker ↔ Employer/Client communication                    │     │
│  └──────────────────────────────────────────────────────────────┘     │
│                                                                       │
└───────────────────────────────────────────────────────────────────────┘
                                   │
                                   │
┌──────────────────────────────────▼────────────────────────────────────── ┐
│                         STORAGE LAYER                                    │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │                    Amazon S3                               │          │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │          │
│  │  │   Original   │  │  Compressed  │  │   Thumbnail  │      │          │
│  │  │    Videos    │  │    Videos    │  │    Images    │      │          │
│  │  │ (Lifecycle → │  │  (CloudFront │  │              │      │          │
│  │  │  Glacier)    │  │   Cached)    │  │              │      │          │
│  │  └──────────────┘  └──────────────┘  └──────────────┘      │          │
│  │                                                            │          │
│  │  • S3 Intelligent-Tiering (cost optimization)              │          │
│  │  • S3 Transfer Acceleration (faster uploads from India)    │          │
│  └────────────────────────────────────────────────────────────┘          |
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │              Amazon DynamoDB                               │          │
│  │  • Worker profiles & skill scores                          │          │
│  │  • Job & contract postings & matches                       │          │
│  │  • Trust scores & ratings                                  │          │
│  │  • Real-time updates (low latency)                         │          │
│  │  • Global tables for multi-region support                  │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │              Amazon RDS (PostgreSQL)                       │          │
│  │  • Transaction history                                     │          │
│  │  • Escrow payment records                                  │          │
│  │  • Audit logs                                              │          │
│  │  • Read replicas for analytics                             │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
                                   │
                                   │
┌──────────────────────────────────▼────────────────────────────────────── ┐
│                    INTEGRATION LAYER                                     │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │              Amazon EventBridge                            │          │
│  │  • Event-driven workflows                                  │          │
│  │  • Job & contract matching triggers                        │          │
│  │  • Payment processing events                               │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │              Amazon SQS                                    │          │
│  │  • Video processing queue                                  │          │
│  │  • Async task handling                                     │          │
│  │  • Retry logic for failed operations                       │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │              Amazon SNS                                    │          │
│  │  • Push notifications (job & contract matches, payments)  │          │
│  │  • SMS alerts (low-data fallback)                          │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │         Payment Gateway Integration                        │          │
│  │  • Razorpay / Paytm API                                    │          │
│  │  • UPI integration                                         │          │
│  │  • Bank transfer APIs                                      │          │
│  │  • Escrow management                                       │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
                                   │
                                   │
┌──────────────────────────────────▼────────────────────────────────────── ┐
│                  MONITORING & SECURITY LAYER                             │
├──────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │              Amazon CloudWatch                             │          │
│  │  • Application logs                                        │          │
│  │  • Performance metrics                                     │          │
│  │  • Cost monitoring                                         │          │
│  │  • Alarms & alerts                                         │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │              AWS IAM & Cognito                             │          │
│  │  • User authentication (workers & employers/clients)       │          │
│  │  • Role-based access control                               │          │
│  │  • Social login (Google, Phone OTP)                        │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
│  ┌────────────────────────────────────────────────────────────┐          │
│  │              AWS WAF & Shield                              │          │
│  │  • DDoS protection                                         │          │
│  │  • Bot detection                                           │          │
│  │  • Rate limiting                                           │          │
│  └────────────────────────────────────────────────────────────┘          │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## Key Design Decisions

### 1. Low Bandwidth Optimization
- **CloudFront CDN**: Caches videos at edge locations across India, reducing latency and bandwidth
- **S3 Transfer Acceleration**: Speeds up video uploads from rural areas
- **Adaptive bitrate**: Videos compressed to multiple quality levels (240p, 480p, 720p)
- **Thumbnail previews**: Show image previews before loading full video
- **Offline-first app**: Flutter app with local SQLite cache for offline viewing

### 2. Cost Efficiency
- **Serverless architecture**: Pay only for actual usage (Lambda, API Gateway)
- **S3 Intelligent-Tiering**: Automatically moves old videos to cheaper storage
- **DynamoDB on-demand**: No need to provision capacity upfront
- **Spot instances**: For batch video processing jobs (optional)
- **Estimated monthly cost**: $200-500 for 10,000 active users

### 3. Scalability
- **Auto-scaling**: Lambda scales automatically to millions of requests
- **DynamoDB**: Handles millions of reads/writes per second
- **SQS queues**: Decouples video processing from API requests
- **Multi-region**: Can deploy to Mumbai + Hyderabad regions for redundancy

### 4. Multilingual Support
- **Amazon Transcribe**: Supports 12+ Indian languages out-of-the-box
- **Amazon Translate**: Real-time translation between worker and employer
- **Bedrock LLMs**: Context-aware translation for trade-specific terminology

---

## Data Flow Examples

### Worker Onboarding Flow
```
1. Worker records video → Flutter app compresses locally
2. Upload to S3 via Transfer Acceleration
3. S3 event triggers Lambda → adds job to SQS queue
4. Lambda processes video:
   - Rekognition: Analyzes tools, safety compliance
   - Transcribe: Converts voice to text
   - Bedrock: Extracts skill metadata
5. Results stored in DynamoDB
6. Worker gets "Skill Trust Score" via SNS notification
```

### Job & Contract Matching Flow
```
1. Employer/client posts job or contract via voice note
2. API Gateway → Lambda
3. Transcribe: Voice → Text
4. Translate: Employer/client language → Worker language
5. Bedrock: AI matches top 3 workers based on:
   - Skill score
   - Location proximity
   - Past ratings
6. Workers receive push notification (SNS)
7. Worker accepts → Escrow payment initiated
```

### Payment Flow
```
1. Employer/client deposits to escrow (Razorpay API)
2. Worker completes task → uploads proof video
3. Rekognition verifies task completion
4. Employer/client approves (or AI auto-approves after 48h)
5. Lambda triggers payment release
6. Funds transferred to worker's bank account
7. Both parties rate each other → Trust Score updated
```

---

## Cost Breakdown (Estimated for 10,000 active users/month)

| Service | Usage | Monthly Cost |
|---------|-------|--------------|
| **Lambda** | 5M requests, 512MB, 3s avg | $25 |
| **API Gateway** | 5M API calls | $18 |
| **S3** | 500GB storage, 1TB transfer | $35 |
| **CloudFront** | 2TB data transfer | $85 |
| **DynamoDB** | 10M reads, 2M writes | $15 |
| **RDS (PostgreSQL)** | db.t3.small | $30 |
| **Bedrock** | 1M tokens/month | $50 |
| **Rekognition** | 10K videos analyzed | $40 |
| **Transcribe** | 5K hours | $75 |
| **Translate** | 1M characters | $15 |
| **SNS/SQS** | 1M notifications | $5 |
| **CloudWatch** | Logs & metrics | $10 |
| **Total** | | **~$403/month** |

**Cost per user**: ~$0.04/month (highly scalable)

---

## Security Considerations

1. **Data encryption**: All data encrypted at rest (S3, DynamoDB, RDS) and in transit (TLS)
2. **IAM roles**: Least-privilege access for all Lambda functions
3. **Cognito**: Secure authentication with MFA for employers
4. **WAF rules**: Block malicious traffic and bots
5. **Audit logs**: All transactions logged to RDS for compliance
6. **PII protection**: Worker phone numbers hashed, videos watermarked

---

## Futrue Deployment Strategy

### Phase 1: MVP (Month 1-2)
- Single region (Mumbai)
- 1,000 beta users
- Basic video upload + skill verification
- Manual payment processing

### Phase 2: Scale (Month 3-6)
- Multi-region (Mumbai + Hyderabad)
- 10,000 users
- Automated escrow payments
- AI-powered job matching

### Phase 3: Production (Month 6+)
- Pan-India deployment
- 100,000+ users
- Advanced fraud detection
- Integration with government schemes (PM-KISAN, MGNREGA)

---

## Alternative Architecture (Lower Cost)

For even lower costs during MVP phase:

- Replace RDS with DynamoDB (fully serverless)
- Use S3 + Lambda instead of CloudFront initially
- Start with fewer Bedrock models (only Claude 3)
- Use Amazon Polly instead of Translate for basic voice responses
- Estimated cost: **~$150/month** for 1,000 users

---

## Monitoring & Alerts

Key metrics to track:
- Video upload success rate
- Average video processing time
- API response times (p50, p95, p99)
- Cost per transaction
- User engagement (daily active users)
- Trust score distribution

CloudWatch alarms for:
- Lambda errors > 1%
- API Gateway 5xx errors
- S3 upload failures
- Payment processing failures
- Bedrock throttling

---

## Next Steps

1. Set up AWS account with appropriate IAM roles
2. Deploy infrastructure using AWS CDK or Terraform
3. Configure Bedrock model access (request quota increases)
4. Set up CI/CD pipeline (AWS CodePipeline)
5. Load test with synthetic data
6. Pilot with 100 workers in one district

