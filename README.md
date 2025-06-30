# Pop Culture KQL Datasets

This repository contains fictional datasets inspired by popular fictional universes—Star Wars and Harry Potter—designed for learning and experimenting with the Kusto Query Language (KQL) in Azure Data Explorer. These datasets were created to accompany the blog post "KQL in Pop Culture: Querying Your Favorite Fictional Worlds."

## Datasets

### 1. SmugglerLogs.csv
**Description**: A dataset of smuggling activities in the Star Wars universe, tracking smugglers, cargo types, planets, and quantities.

**Schema**:
- `Timestamp` (datetime): Date and time of the smuggling activity (ISO 8601 format, e.g., `2023-01-01T08:00:00`).
- `Smuggler` (string): Name of the smuggler (e.g., Han Solo, Lando Calrissian).
- `CargoType` (string): Type of cargo (e.g., Spice, Blasters, Kyber Crystals).
- `Planet` (string): Planet where the activity occurred (e.g., Tatooine, Corellia).
- `Quantity` (int): Amount of cargo smuggled.

**Size**: 100 records.

**Example Use Cases**:
- Find the most active smugglers by activity count.
- Analyze smuggling trends by cargo type or planet.

### 2. PotionsGrades.csv
**Description**: A dataset of student performance in Potions class at Hogwarts School of Witchcraft and Wizardry, including grades and scores.

**Schema**:
- `AcademicYear` (int): Year of the record (e.g., 1995).
- `Student` (string): Student’s name (e.g., Hermione Granger, Harry Potter).
- `House` (string): Hogwarts house (e.g., Gryffindor, Slytherin).
- `Potion` (string): Name of the potion brewed (e.g., Draught of Peace, Polyjuice Potion).
- `Grade` (string): Grade received (e.g., Outstanding, Acceptable).
- `Score` (int): Numerical score out of 100.

**Size**: 80 records.

**Example Use Cases**:
- Calculate average scores by Hogwarts house.
- Identify top students for specific potions.

## How to Use

1. **Download the Datasets**:
   - Clone this repository: `git clone <repository-url>`
   - Or download the CSV files directly from the GitHub repository by navigating to the files and clicking "Download".

2. **Set Up Azure Data Explorer**:
   - Create a free cluster at [dataexplorer.azure.com](https://dataexplorer.azure.com).
   - Create two tables, `SmugglerLogs` and `PotionsGrades`, with the schemas described above.

3. **Ingest the Data**:
   - Use the Azure Data Explorer web UI to ingest the CSV files:
     - For `SmugglerLogs.csv`, map columns to the schema: `Timestamp` (datetime), `Smuggler` (string), `CargoType` (string), `Planet` (string), `Quantity` (int).
     - For `PotionsGrades.csv`, map columns to: `AcademicYear` (int), `Student` (string), `House` (string), `Potion` (string), `Grade` (string), `Score` (int).
   - Alternatively, use KQL ingestion commands (see Azure Data Explorer documentation).

4. **Run KQL Queries**:
   - Refer to the blog post for sample KQL queries, such as finding the most active smugglers or analyzing potion class performance trends.
   - Example query for `SmugglerLogs`:
     ```kql
     SmugglerLogs
     | summarize ActivityCount = count() by Smuggler
     | order by ActivityCount desc
     | top 3 by ActivityCount
     ```
   - Example query for `PotionsGrades`:
     ```kql
     PotionsGrades
     | summarize AvgScore = avg(Score) by House
     | order by AvgScore desc
     ```

## Notes
- The datasets are fictional and created for educational purposes.
- Timestamps in `SmugglerLogs` are in UTC and span early 2023.
- `PotionsGrades` covers academic years 1995–1997, inspired by the Harry Potter timeline.
- For larger datasets, you can generate additional records using Python or other tools (e.g., Faker library).

## License
This dataset is provided under the MIT License. Feel free to use, modify, and share it for educational or personal projects.

## Contact
For questions or feedback, open an issue in this repository or refer to the blog post for more context.

Happy querying, and may the Force (and data) be with you!
