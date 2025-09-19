# Reliable Parse Standard: Wellness Tracking Protocol

A blockchain-enabled wellness tracking smart contract that provides secure, privacy-preserving health metric management with adaptive achievement systems and comprehensive data validation.

## Overview

Reliable Parse Standard is a blockchain-powered health tracking protocol that supports comprehensive monitoring of three pivotal wellness dimensions:
- Sleep performance
- Hydration optimization
- Mindfulness engagement

Key Protocol Features:
- Adaptive goal configuration
- Immutable activity logging
- Dynamic achievement mechanisms
- Intelligent wellness scoring
- Cryptographically secured data management
- Persistent activity progression tracking

## Architecture

The Reliable Parse Standard protocol implements a sophisticated smart contract for holistic health tracking:

```mermaid
graph TD
    A[User] -->|Submits Health Data| B[Wellness Tracker Contract]
    B --> C[User Profiles]
    B --> D[Metric Repositories]
    B --> E[Personal Objectives]
    B --> F[Achievement Framework]
    B -->|Computes| G[Wellness Intelligence]
    B -->|Monitors| H[Progression Continuity]
```

The contract implements several key data structures:
- `users`: Stores user profiles and wellness scores
- `daily-metrics`: Records daily health activities
- `user-goals`: Maintains personal wellness targets
- `user-achievements`: Tracks earned achievements
- `achievement-definitions`: Defines available badges and requirements

## Contract Documentation

### Core Functionality

#### User Management
- User profiles are automatically created on first interaction
- Tracks join date, wellness score, and activity streaks
- Privacy-preserving design with principal-based identification

#### Metrics Tracking
- Records daily sleep hours (0-24)
- Monitors water intake in milliliters (0-10000)
- Tracks meditation minutes (0-1440)
- Prevents overwriting of same-day entries

#### Achievement System
Three categories of achievements:
1. Streak-based (7, 30, 100 days)
2. Wellness score milestones (50, 75, 90 points)
3. Goal completion tracking

## Getting Started

### Prerequisites
- Clarinet
- Stacks wallet for testing

### Basic Usage

1. Configure Health Objectives:
```clarity
(contract-call? .wellness-tracker configure-health-objectives 
    u8   ;; targeted sleep duration
    u2000  ;; hydration volume goal
    u20)  ;; mindfulness duration target
```

2. Log Daily Wellness:
```clarity
(contract-call? .wellness-tracker log-daily-wellness 
    u7   ;; actual sleep hours
    u1500  ;; water intake volume
    u15)  ;; meditation duration
```

## Function Reference

### Public Functions

#### `set-wellness-goals`
Sets personal wellness targets
```clarity
(set-wellness-goals sleep-hours-goal water-ml-goal meditation-minutes-goal)
```

#### `record-daily-metrics`
Records all daily wellness metrics
```clarity
(record-daily-metrics sleep-hours water-ml meditation-minutes)
```

#### `update-single-metric`
Updates a single metric value
```clarity
(update-single-metric metric-type value)
```

### Read-Only Functions

#### `get-user-profile`
```clarity
(get-user-profile user) ;; Returns user's profile information
```

#### `get-daily-metrics`
```clarity
(get-daily-metrics user date) ;; Returns metrics for specific date
```

#### `get-user-achievements`
```clarity
(get-user-achievements user) ;; Returns list of earned achievements
```

## Development

### Testing
1. Clone the repository
2. Install Clarinet
3. Run tests:
```bash
clarinet test
```

### Local Development
1. Start Clarinet console:
```bash
clarinet console
```
2. Deploy contract:
```clarity
(contract-call? .wellness-tracker initialize-protocol-achievements)
```

## Security Considerations

### Data Privacy
- All data is associated with user principals
- No direct access to other users' data
- Immutable history of wellness records

### Limitations
- Daily metrics can only be recorded once per day
- Metric values have reasonable upper limits
- Achievement badges cannot be revoked once earned

### Best Practices
- Always validate metric values before submission
- Regular backups of achievement records
- Monitor wellness score calculations for accuracy