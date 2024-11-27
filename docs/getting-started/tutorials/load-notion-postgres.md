## Loading Notion Data To PostgreSQL Database Using Bruin
Welcome! 👋 This tutorial is a simple, step-by-step guide to help you load data from Notion into a PostgreSQL database using Bruin.
Notion is an incredibly versatile tool for organizing projects, taking notes, and managing databases.
However, when you want to leverage this data for analytics, reporting, or integration with other systems, you often need to move it into a structured database like PostgreSQL.
That’s where Bruin comes in. Bruin makes it easy to automate and manage data pipelines, letting you move data from Notion (and other sources) to destinations like PostgreSQL with minimal effort.

If you’re just starting out, don’t worry—this guide is designed for beginners. You’ll learn the basics of setting up a Bruin project, creating a pipeline,
and connecting Notion with PostgreSQL. By the end, you’ll have a working example that you can extend or customize for your own needs.

### Prerequisites
#### Bruin CLI

To install Bruin CLI depending upon your machine, follow the installation instructions [here](https://github.com/bruin-data/bruin/blob/f799133136aba1b0eea673d731f236a4b5e78752/docs/getting-started/introduction/installation.md)

#### Bruin VSCode Extension
To install bruin vscode extension, follow the instruction [here](https://github.com/bruin-data/bruin/blob/f799133136aba1b0eea673d731f236a4b5e78752/docs/vscode-extension/installation.md)

<img width="685" alt="bruin_extension" src="https://github.com/user-attachments/assets/c74607e8-b822-4927-a100-bfe29446101b">


### Getting Started

To create a bruin project basic structure you can just run


   ```
   bruin init {folder name} [template name]
   ```

If you don't define folder name and template name. It will create `default` template with folder name bruin-pipeline. This command will:

    Create a project named bruin-pipeline 
    Generate a folder called bruin-pipeline containing the following:
        -  An assets folder (where you add asset file)
        - .bruin.yml file (where connection and credentials are added)
        -  pipeline.yml file to manage your pipeline

#### Adding a new asset

Adding a new [asset](https://bruin-data.github.io/bruin/assets/ingestr.html) is as simple as creating a new file inside the assets folder. Let's create a new [ingestr asset](https://bruin-data.github.io/bruin/assets/ingestr.html) file `asset.ingetsr.notion.yml` inside assets folder and add :

 ```
name: public.notion
type: ingestr
connection: my-postgres
parameters:
  source_connection: my-notion
  source_table: 'database_id'
  destination: postgres
 ```

- name: The name of the asset.

- type: Specifies the type of the asset. It will be always ingestr type for Notion.

- connection: The name of the connection

- source_connection: The name of the Notion connection defined in .bruin.yml.
- source_table: The database id of Notion you want to ingest.
- destination: The name of the destination, you want to store. Here, we are using postgres sql


#### Adding connection and credentials in .bruin.yml
Make sure, you have [Notion credentials](https://dlthub.com/docs/dlt-ecosystem/verified-sources/notion#setup-guide) and Postgres credentials.

Using Bruin vscode extension
- Add destination connection - PostgresSQL
- Add source connection - Notion

<video width="685" height="auto" controls poster="https://github.com/user-attachments/assets/7f9bac4d-a8d4-4bbf-b114-948ca561f50b">
  <source src="https://github.com/user-attachments/assets/7ef731e3-386a-420c-9355-01bb307436f7" type="video/mp4">
  Your browser does not support the video tag.
</video>


You can customize your pipeline by adding in pipeline.yml
- You can change schedule to daily, weekly or monthly.

#### Validate and Run your pipeline
- bruin CLI can run the whole pipeline or any task with the downstreams.
  `Make sure, asset file is open`

<video width="685" height="auto" controls poster="https://github.com/user-attachments/assets/6fe545f3-8112-4ce2-ac96-3abf6dc1021e">
  <source src="https://github.com/user-attachments/assets/aa6b2c0f-e480-48a5-9975-286af1ab4474" type="video/mp4">
  Your browser does not support the video tag.
</video>



#### This is what Notion data looks like at the destination:
<br>
<img width="968" alt="notion_dest" src="https://github.com/user-attachments/assets/bdf4f4af-30b9-44a9-bd32-ba004ad501d5">


🎉 Congratulations!

You've successfully created and run your first Bruin pipeline! Your Notion data is now ingested into PostgreSQL, ready for you to query and explore. This is just the beginning—feel free to extend this pipeline, add more data sources, or incorporate data transformations to suit your needs.

For more advanced features and customization, check out the Bruin documentation.

Happy data engineering! 🚀
