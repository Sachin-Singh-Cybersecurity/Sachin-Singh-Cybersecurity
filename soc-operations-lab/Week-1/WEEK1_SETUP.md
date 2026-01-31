# Week 1: SIEM Setup

**Date**: January 21-February 2, 2026
# 
## Project Goal
Build working Splunk environment with basic log ingestion

## What I Did

### Day 1: Installation & First Data
1. Downloaded Splunk Enterprise Edition
2. Installed on local machine
3. Accessed web interface at localhost:8000
4. Created test index `lab-test`
5. Uploaded sample logs
6. Verified data ingestion with basic search

### Configuration
- Splunk Version: Enterprise Edition
- Index: lab-test (500MB limit for testing)
- Data Source: Sample log files
- Access: localhost:8000

### Screenshots
Screenshot 1: Splunk home page (after login)
Screenshot 2: Indexes configured
Screenshot 3: Search results

## Next Steps
- Add Windows system logs
- Add Linux syslog
- Create dashboards
- Set up basic alerts

## Learning Notes
- Splunk is running on default port 8000
- Index stores data in buckets
- Search uses SPL (Splunk Processing Language)
- Community Edition has 500MB/day limit
