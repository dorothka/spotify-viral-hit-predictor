# 🎵 The Spotify Viral Hit Predictor

**Role:** Data Strategy Consultant | **Tech Stack:** Python, SQL, Tableau

## 🚀 Project Overview
In this project, I analyzed **114,000 Spotify Tracks** to figure out exactly what makes a song go viral. I used Python and SQL to clean the data and Tableau to visualize the results. The goal was to tell a record label exactly how to produce a hit in 2025.

## 📊 The Dashboard
### [👉 Click Here to View the Interactive Dashboard](https://public.tableau.com/views/SpotifyDataAnalysisTheViralHitPredictor/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

## 🎧 The 2025 Hit Formula (Key Findings)
* **Keep It Short:** Attention spans are short. The data shows the sweet spot is strictly **2.5 to 3.5 minutes**. If the song drags on past 4 minutes, listeners drop off.
* **Any Vibe Works:** There is no "magic genre" right now. Sad songs, party anthems, and chill tracks are all equally popular. You do not need to chase a specific mood to win.
* **The Strategy:** Focus on the timing rather than the genre. Make it punchy and get to the chorus quickly.

## 🛠️ Technical Process
1.  **Data Hybridization:** I combined raw Kaggle data with human-labeled ratings in Google Sheets to simulate real-world data enrichment.
2.  **The Logic Engine (Python/SQL):**
    * Loaded data into a temporary SQL database.
    * Used SQL logic to categorize songs into "Vibes" (Party vs. Sad) based on energy and valence.
    * Filtered out glitchy data and dead tracks.
3.  **Visualization:** Built an interactive Tableau dashboard to prove the findings.

## 💻 Code Snippet (SQL Logic)
```sql
/* Logic to categorize songs into "Vibes" 
   based on audio energy and happiness (valence)
*/

SELECT
    track_name,
    (duration_ms / 60000.0) as duration_minutes,
    CASE
        WHEN valence > 0.6 AND energy > 0.6 THEN 'Party Anthem'
        WHEN valence < 0.4 AND energy < 0.4 THEN 'Sad/Moody'
        ELSE 'Chill/Casual'
    END as Vibe_Category
FROM tracks
WHERE popularity >= 1
ORDER BY popularity DESC;
