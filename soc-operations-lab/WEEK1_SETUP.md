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
Screenshot 1: Splunk home page (after login)\
Screenshot 2: Indexes configured\
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

### Day 2: Multi-Source Ingestion & Dashboard

**Date:** January 22, 2026

**What I Did:**
1. Created 3 dedicated indexes:
   - lab-windows (Windows Event Logs)
   - lab-linux (Linux syslog)
   - lab-web (Web server access logs)

2. Uploaded sample logs:
   - Windows Security/Application logs (2661 events)
   - Linux syslog and auth.log (2000 events)
   - Apache/IIS access logs (1744 events)

3. Created first dashboard "Lab Overview":
   - Events by log source (pie chart)
   - Event timeline (line chart)
   - Top 10 sources (bar chart)

**Configuration:**
- Total Indexes: 4 (lab-test, lab-windows, lab-linux, lab-web)
- Total Events Ingested: 16,405
- Dashboard: Lab Overview (3 panels)

**Screenshots:**
- Day2_indexes.png
- Day2_windows_logs.png
- Day2_linux_logs.png
- Day2_web_logs.png
- Day2_dashboard.png

**What I Learned:**
- Index organization best practices
- Multiple source types in single SIEM
- Dashboard creation workflow
- SPL (Splunk Processing Language) basics:
  - `stats count by field`
  - `timechart` for timeline viz
  - `sort` and `head` for top N

**Next Steps:**
- Add real-time Windows logs (monitor, not upload)
- Create alerts on suspicious activity
- Build correlation searches
- Add more sophisticated visualizations
