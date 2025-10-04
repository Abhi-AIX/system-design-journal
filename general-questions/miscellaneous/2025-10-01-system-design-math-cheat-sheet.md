# System Design Math – Cheat Sheet

This is simple one-page cheat sheet to quickly estimate scale in system design interviews and real-world planning.  
It covers **orders of magnitude, time units, storage, and networking.**  

---

## Order of Magnitude
- 10 = 10¹ → ten  
- 100 = 10² → hundred  
- 1,000 = 10³ → thousand  
- 10,000 = 10⁴ → ten thousand  
- 100,000 = 10⁵ → hundred thousand  
- 1,000,000 = 10⁶ → million  
- 10,000,000 = 10⁷ → ten million  
- 100,000,000 = 10⁸ → hundred million  
- 1,000,000,000 = 10⁹ → billion  
- 1,000,000,000,000 = 10¹² → trillion  

---

## Time
- 1 ns = 10⁻⁹ sec  
- 1 µs = 10⁻⁶ sec  
- 1 ms = 10⁻³ sec  
- 1 sec = 1,000 ms  
- 1 minute = 60 sec  
- 1 hour = 60 minutes = 3,600 sec  
- 1 day = 24 hours = 86,400 sec  
- 1 month (30 days) ≈ 2.6 million sec  
- 1 year (365 days) ≈ 31.5 million sec  

**Human scale:**  
- <100 ms feels *instant*  
- ~1 sec feels *laggy*  

**System scale:**  
- µs/ns → hardware performance  
- ms → API calls / DB queries  
- sec/min/hr → jobs & workflows  

---

## Storage & Data Units
- 1 byte (B) = 8 bits (b)  
- 1 KB (kilobyte) = 1,000 bytes  
- 1 MB (megabyte) = 1,000 KB ≈ 1 million bytes  
- 1 GB (gigabyte) = 1,000 MB ≈ 1 billion bytes  
- 1 TB (terabyte) = 1,000 GB ≈ 1 trillion bytes  
- 1 PB (petabyte) = 1,000 TB  
- 1 EB (exabyte) = 1,000 PB  

**Useful examples:**  
- 1 KB → small JSON request, log entry  
- 1 MB → image, DB row batch  
- 1 GB → movie file, daily logs for small service  
- 1 TB → monthly logs for big app  
- 1 PB → ML training / analytics dataset  

---

## Networking Units
- bit (b) = smallest unit of data (0 or 1)  
- Byte (B) = 8 bits  
- bps = bits per second (bandwidth measure)  

**Common scales:**  
- Kbps = 10³ bps  
- Mbps = 10⁶ bps  
- Gbps = 10⁹ bps  
- Tbps = 10¹² bps  

**Rules of thumb:**  
- 1 MB/s ≈ 8 Mbps  
- LAN (data centers): ~1–10 Gbps  
- WAN (Internet): 10 Mbps (slow) → 1 Gbps (fiber)  
- Cloud NICs: 100 Mbps (small) → 10–100 Gbps (big)  