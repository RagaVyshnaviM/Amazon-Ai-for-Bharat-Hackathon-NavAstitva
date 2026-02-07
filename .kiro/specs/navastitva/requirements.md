# Requirements Document: NavAstitva
*A new beginning with dignity and purpose*

## Introduction

NavAstitva is a multilingual, video-first platform that empowers rural and informal skilled workers in India by connecting them with employers/clients through AI-powered skill verification and matchmaking. The platform goes beyond traditional job boards by offering:

- **Escrow-based secure payments** to ensure fair wages
- **Job and contract posting** for employers/clients, creating transparent work opportunities and freelance contracts
- **Skill trust card** for workers, showcasing verified skills that can open doors to multiple opportunities across sectors
- **Voice-activated interfaces and assisted onboarding** to bridge the digital divide
- **Offline support and AI-driven trust ratings** to build confidence between workers and employers/clients

By combining skill verification, secure payments, and discoverable skill profiles, NavAstitva not only connects workers to immediate jobs and freelance contracts but also empowers them for future business opportunities and long-term career growth.

## Target Audience

### Workers

Our platform empowers skilled rural workers to access verified job opportunities, freelance contracts and fair pay. It serves a wide range of workers, such as:

- **Carpenters, craftsmen, decorators**
- **Women cooks, home chefs, delivery personnel**
- **Electricians, plumbers, tutors, and other local service providers**

### Employers / Clients

Businesses, SMEs, or individual clients who need trusted, skilled workers for jobs or freelance contracts. They benefit from:

- **Access to verified talent** through AI skill verification
- **Job and contract posting** for quick hiring
- **Trust scores and skill cards** to make informed hiring decisions
- **Secure escrow payments** ensuring transparent transactions

### Why This Matters for Bharat ?

India's rural skilled workforce—comprising artisans, electricians, carpenters, cooks, and countless other trades—represents the backbone of our nation's economy. Yet these skilled individuals face systemic barriers that prevent them from accessing fair opportunities:

**The Challenge:**
- **Digital Exclusion**: Over 65% of India's population lives in rural areas, where digital literacy and English proficiency are limited. Traditional job platforms require formal resumes and English skills, automatically excluding millions of capable workers from jobs and freelance contracts.
- **Trust Deficit**: Without formal credentials or verifiable work history, skilled workers struggle to prove their capabilities to distant employers/clients, leading to exploitation by middlemen who take 20-30% commissions.
- **Economic Inequality**: Rural workers often earn 40-50% less than their urban counterparts for the same skills, not due to lack of ability, but lack of access to fair-paying jobs, contracts, and business opportunities.
- **Dignity Gap**: The absence of portable, verifiable credentials means workers must repeatedly prove themselves, undermining their dignity and professional identity.

**The Opportunity:**
NavAstitva leverages India's growing smartphone penetration (750+ million users) and expanding 4G/5G networks to create an inclusive platform that:
- **Preserves Dignity**: Workers showcase skills through video demonstrations in their own language, maintaining pride in their craft
- **Builds Trust**: AI-powered verification creates objective skill assessments, replacing subjective bias with data-driven trust scores
- **Ensures Fairness**: Transparent wage recommendations and escrow payments protect workers from exploitation
- **Enables Mobility**: Portable Skill Trust Cards allow workers to carry their verified reputation across platforms and geographies

**Impact on Bharat:**
By empowering rural skilled workers with technology that respects their language, literacy levels, and connectivity constraints, NavAstitva can:
- Increase rural incomes by 30-40% through direct employer/client connections and freelance contracts
- Create economic opportunities for 100+ million skilled workers across India through jobs and business opportunities
- Reduce urban migration pressure by enabling remote work opportunities and freelance contracts
- Preserve traditional crafts and skills by making them economically viable
- Strengthen the dignity of manual labor in Indian society

This is not just a platform—it's a movement toward economic justice and social dignity for the skilled workers who build Bharat.

## Glossary

- **Worker**: A rural skilled worker (artisan, electrician, carpenter, cook, etc.) seeking employment opportunities, freelance contracts, and business opportunities
- **Employer/Client**: An individual, business, or organization seeking to hire skilled workers for jobs or freelance contracts
- **Job_Contract_Poster**: An employer/client who posts job or contract opportunities on the platform
- **Skill_Trust_Engine**: The AI system that analyzes videos, verifies skills, and generates trust scores
- **Living_Resume**: A video-based portfolio showcasing a worker's skills through demonstration videos
- **Skill_Trust_Card**: A portable digital credential containing a worker's verified skills and trust score
- **Trust_Score**: A numerical rating (0-100) based on skill verification, reviews, and performance history
- **Onboarding_Assistant**: NGO or Panchayat representative helping workers register on the platform
- **Escrow_System**: Payment holding mechanism that releases funds after work verification
- **Phygital_Model**: Hybrid physical-digital approach combining enrollment booths with digital platform
- **Voice_Interface**: Multilingual voice-activated user interface supporting 12+ Indian languages
- **Offline_Mode**: Capability to record and view content without internet connectivity
- **AI_Matchmaking_Engine**: System that matches workers to jobs and contracts based on skills, location, and trust scores
- **Video_Verification_System**: Computer vision system analyzing skill demonstration videos
- **Fair_Wage_Engine**: AI system recommending wages based on market rates, location, and skill level

## Requirements

### Requirement 1: Worker Video Profile Creation

**User Story:** As a worker, I want to create a video-based skill profile in my local language, so that I can showcase my abilities to potential employers/clients without needing formal documentation.

#### Acceptance Criteria

1. WHEN a worker uploads a skill demonstration video, THE Video_Verification_System SHALL accept videos between 30 seconds and 5 minutes in duration
2. WHEN a worker records voice narration, THE Voice_Interface SHALL support recording in any of 12+ Indian languages (Hindi, Tamil, Telugu, Bengali, Marathi, Gujarati, Kannada, Malayalam, Punjabi, Odia, Assamese, Urdu)
3. WHEN a video is uploaded, THE Skill_Trust_Engine SHALL process the video within 2 minutes and extract skill indicators
4. WHERE offline mode is enabled, THE Offline_Mode SHALL store videos locally and sync automatically when connectivity is restored
5. WHEN a worker completes their profile, THE Living_Resume SHALL display all uploaded skill videos with timestamps and language tags

### Requirement 2: Assisted Onboarding via Phygital Model

**User Story:** As a worker with limited digital literacy, I want assistance from local representatives to register on the platform, so that I can access opportunities despite my lack of technical skills.

#### Acceptance Criteria

1. WHEN an Onboarding_Assistant initiates registration, THE System SHALL provide a simplified enrollment interface with voice guidance
2. WHEN biometric data is captured, THE System SHALL store Aadhaar-linked identity verification securely with encryption
3. WHEN an Onboarding_Assistant uploads documents on behalf of a worker, THE System SHALL associate those documents with the worker's profile
4. WHEN registration is complete, THE System SHALL generate a unique Worker ID and send confirmation via SMS in the worker's preferred language
5. WHERE enrollment occurs at a Panchayat booth, THE System SHALL function with intermittent connectivity and queue operations for later sync

### Requirement 3: Multilingual Voice-Activated Interface

**User Story:** As a worker who is not literate in English, I want to navigate the platform using voice commands in my local language, so that I can use the platform independently.

#### Acceptance Criteria

1. WHEN a worker speaks a command, THE Voice_Interface SHALL recognize and execute commands in the worker's selected language with 90% accuracy
2. WHEN the system responds, THE Voice_Interface SHALL provide audio feedback in the same language as the input
3. WHEN a worker switches languages, THE Voice_Interface SHALL update all UI text and audio prompts to the new language within 1 second
4. WHEN voice input fails, THE Voice_Interface SHALL provide visual fallback options with icons and minimal text
5. WHEN background noise is detected, THE Voice_Interface SHALL prompt the worker to repeat the command or move to a quieter location

### Requirement 4: AI-Powered Skill Verification

**User Story:** As an employer/client, I want AI-verified skill assessments of workers, so that I can trust the capabilities shown in their profiles without in-person verification.

#### Acceptance Criteria

1. WHEN a skill video is analyzed, THE Video_Verification_System SHALL identify correct tool usage, safety protocols, and technique quality
2. WHEN analysis is complete, THE Skill_Trust_Engine SHALL generate a skill-specific score (0-100) based on video analysis
3. WHEN multiple videos exist for the same skill, THE Skill_Trust_Engine SHALL compute an aggregate skill score weighted by recency
4. WHEN video authenticity is questionable, THE Video_Verification_System SHALL flag potential fraud or plagiarism for manual review
5. WHEN a Trust_Score is calculated, THE Skill_Trust_Engine SHALL combine video analysis scores (40%), employer/client ratings (40%), and completion history (20%)

### Requirement 5: Skill Trust Card Generation

**User Story:** As a worker, I want a portable digital credential showing my verified skills and ratings, so that I can prove my capabilities across multiple platforms and contexts.

#### Acceptance Criteria

1. WHEN a worker completes at least one verified skill video, THE System SHALL generate a Skill_Trust_Card containing worker ID, skills, and Trust_Score
2. WHEN the Skill_Trust_Card is accessed, THE System SHALL display a QR code that employers/clients can scan for instant verification
3. WHEN an employer/client scans the QR code, THE System SHALL display the worker's verified skills, Trust_Score, and recent reviews
4. WHEN a worker's Trust_Score changes, THE Skill_Trust_Card SHALL update automatically within 1 hour
5. WHERE offline access is needed, THE Skill_Trust_Card SHALL be downloadable as a PDF with embedded QR code

### Requirement 6: Job & Contract Posting

**User Story:** As a job & contract poster, I want to post job or contract requirements using voice or text in my preferred language, so that I can quickly find suitable workers without complex forms.

#### Acceptance Criteria

1. WHEN a job & contract poster speaks job or contract requirements, THE Voice_Interface SHALL transcribe and structure the posting with skill tags, location, duration, and work type (job/contract)
2. WHEN a posting is created, THE System SHALL require minimum fields: skill type, location, duration, work type (job/contract), and budget range
3. WHEN budget is specified, THE Fair_Wage_Engine SHALL compare it against market rates and suggest adjustments if below fair wage
4. WHEN a posting is submitted, THE AI_Matchmaking_Engine SHALL identify and rank the top 3 matching workers within 30 seconds
5. WHEN multiple languages are used, THE System SHALL translate postings to match worker language preferences

### Requirement 7: AI-Powered Worker Matchmaking

**User Story:** As an employer/client, I want the system to automatically match me with the most suitable workers based on skills, location, and reliability, so that I can save time in the hiring process.

#### Acceptance Criteria

1. WHEN a job or contract is posted, THE AI_Matchmaking_Engine SHALL rank workers based on skill match (40%), Trust_Score (30%), proximity (20%), and availability (10%)
2. WHEN matches are generated, THE System SHALL present the top 3 workers with their profiles, Trust_Scores, and estimated response time
3. WHEN a worker is unavailable, THE AI_Matchmaking_Engine SHALL exclude them from matches and select the next best candidate
4. WHEN location is specified, THE AI_Matchmaking_Engine SHALL prioritize workers within 50km radius
5. WHEN no suitable matches exist, THE System SHALL notify the employer/client and suggest broadening search criteria

### Requirement 8: Secure Escrow-Based Payments

**User Story:** As a worker, I want payment protection through an escrow system, so that I am guaranteed payment after completing work satisfactorily.

#### Acceptance Criteria

1. WHEN an employer/client accepts a worker, THE Escrow_System SHALL hold the agreed payment amount in escrow before work begins
2. WHEN work is marked complete by the worker, THE System SHALL notify the employer/client to verify completion
3. WHEN the employer/client confirms completion, THE Escrow_System SHALL release payment to the worker's bank account within 24 hours
4. IF the employer/client disputes completion, THEN THE System SHALL initiate a review process and hold payment for up to 7 days
5. WHEN payment is released, THE System SHALL send confirmation notifications to both worker and employer/client via SMS

### Requirement 9: Transparent Rating and Review System

**User Story:** As an employer/client, I want to rate workers after job or contract completion, so that future employers/clients can make informed decisions and workers are incentivized to maintain quality.

#### Acceptance Criteria

1. WHEN a job or contract is completed, THE System SHALL prompt the employer/client to provide a star rating (1-5) and optional voice/text review
2. WHEN a review is submitted, THE System SHALL update the worker's Trust_Score within 1 hour
3. WHEN a worker receives a rating below 3 stars, THE System SHALL notify the worker and request improvement feedback
4. WHEN reviews are displayed, THE System SHALL show the most recent 10 reviews with star ratings and timestamps
5. WHEN a review is flagged as inappropriate, THE System SHALL hide it pending manual moderation within 48 hours

### Requirement 10: Fraud Detection and Video Authenticity

**User Story:** As a platform administrator, I want automated fraud detection to identify fake or plagiarized skill videos, so that the platform maintains trust and credibility.

#### Acceptance Criteria

1. WHEN a video is uploaded, THE Video_Verification_System SHALL check for duplicate content across the platform using perceptual hashing
2. WHEN video metadata is analyzed, THE Video_Verification_System SHALL verify that recording timestamp and location are consistent with upload time
3. WHEN deepfake indicators are detected, THE Video_Verification_System SHALL flag the video for manual review
4. WHEN a worker uploads multiple identical videos, THE System SHALL reject duplicates and notify the worker
5. WHEN fraud is confirmed, THE System SHALL suspend the worker's account and notify affected employers/clients

### Requirement 11: Multilingual Translation and Transcription

**User Story:** As an employer/client who speaks a different language than the worker, I want automatic translation of voice content, so that I can understand worker profiles and communicate effectively.

#### Acceptance Criteria

1. WHEN a worker's voice narration is in a different language than the employer/client's preference, THE System SHALL provide real-time translated transcription
2. WHEN translation is displayed, THE System SHALL show both original language and translated text with language labels
3. WHEN voice messages are exchanged, THE System SHALL translate and provide audio playback in the recipient's preferred language
4. WHEN translation confidence is below 80%, THE System SHALL flag the content and suggest manual verification
5. WHEN technical skill terms are translated, THE System SHALL maintain domain-specific terminology accuracy

### Requirement 12: Offline Capability and Sync

**User Story:** As a worker in an area with poor connectivity, I want to record videos and view job and contract postings offline, so that I can use the platform despite network limitations.

#### Acceptance Criteria

1. WHERE connectivity is unavailable, THE Offline_Mode SHALL allow workers to record and store up to 10 videos locally
2. WHEN connectivity is restored, THE Offline_Mode SHALL automatically sync pending videos and profile updates to the server
3. WHERE offline mode is active, THE System SHALL cache the worker's last 20 job and contract matches for offline viewing
4. WHEN sync conflicts occur, THE System SHALL prioritize server data and notify the worker of any local changes that were overwritten
5. WHEN storage is limited, THE Offline_Mode SHALL compress videos to reduce file size while maintaining acceptable quality

### Requirement 13: Fair Wage Recommendation Engine

**User Story:** As a worker, I want the system to recommend fair wages for my skills and location, so that I am not underpaid and can negotiate confidently.

#### Acceptance Criteria

1. WHEN a job or contract posting is created, THE Fair_Wage_Engine SHALL analyze market rates for the skill type, location, and work duration
2. WHEN wage data is insufficient, THE Fair_Wage_Engine SHALL use regional averages and skill category benchmarks
3. WHEN an employer/client's budget is below fair wage, THE Fair_Wage_Engine SHALL display a warning and suggest a minimum fair wage
4. WHEN a worker views a posting, THE System SHALL display the offered wage alongside the recommended fair wage range
5. WHEN wage recommendations are generated, THE Fair_Wage_Engine SHALL update rates monthly based on market trends

### Requirement 14: Worker Availability Management

**User Story:** As a worker, I want to set my availability status and preferred work locations, so that I only receive relevant job and contract matches when I am ready to work.

#### Acceptance Criteria

1. WHEN a worker updates availability, THE System SHALL allow selection of "Available Now", "Available from [date]", or "Not Available"
2. WHEN a worker is marked "Not Available", THE AI_Matchmaking_Engine SHALL exclude them from all job and contract matches
3. WHEN a worker specifies preferred locations, THE System SHALL prioritize matches within those locations
4. WHEN a worker's availability status is unchanged for 30 days, THE System SHALL send a reminder to update status
5. WHEN a worker accepts a job or contract, THE System SHALL automatically update availability to "Busy" until work completion

### Requirement 15: Platform Security and Data Privacy

**User Story:** As a worker, I want my personal information and videos to be securely stored and only shared with verified employers/clients, so that my privacy is protected.

#### Acceptance Criteria

1. WHEN personal data is stored, THE System SHALL encrypt all sensitive information (Aadhaar, bank details, contact info) using AES-256 encryption
2. WHEN a video is uploaded, THE System SHALL store it in a secure S3 bucket with access restricted to authenticated users only
3. WHEN an employer/client views a worker profile, THE System SHALL log the access with timestamp and employer/client ID for audit purposes
4. WHEN a worker deletes their account, THE System SHALL permanently remove all personal data within 30 days per data protection regulations
5. WHEN authentication occurs, THE System SHALL use multi-factor authentication for employer/client accounts and OTP-based verification for worker accounts
