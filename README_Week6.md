Core Scripts for Final Project - Tr8 Plants using R-Programming

In Shell, we will be using the following commands for the following purposes.

echo: Writes an argument to the standard output and displays the new text. This will be useful when stringing data, especially when dealing with variables.

sed: Replace and delete function. Can be used to change words, tabs, numbers, and any other type of data provided. Also useful for deleting duplicate occurances. Could also use the commands "grep" or "awk" for replacing and deleting needs.

Example for creating columns with the data types:

 echo "1st_column%2nd_column%3rd_column..4th_column" > Tr8_Plants_Data.txt   ---   Displays the said columns  
 sed 's/%/\t/g' Tr8_Plants_Data.txt   ---   Separates the columns of data with tabs and keeps their descriptive name
RStudio: Create formatting for the organized data. This could includes changes in font, font size, or color of text. This will also be useful when plotting the data on a graph.

sp: Character, identifies a single species name in a specified form.

gisd: Checks invasive species status for a set of species from GISD Database.

key: Loads data from the RStudio profile, useful for graphing and plotting data.

Example for creating a plot graph with the provided data in RStudio:

 library(Tr8Plants)
 library(Tr8Plants)
 key <- name_backbone(name='Plant Location')$speciesKey
 x <- map_fetch(taxonKey = key)
 plot(x, axes = TRUE, box = TRUE)
RStudio Potential Commands and their Function/Output:

Tr8 Package: A tool for dowloading functional traits, data for plant species.

install.packages("TR8")   ---   How to install a package into RStudio
install_github("roponsci/TR8")  ---  Installs GitHub for pushing analysis
library("TR8")   --- Downloads the specific package required for analysis

url<-"http://datadryad.org/bitstream/handle/+10255/dryad.65646/MEE-13-11-651R2_data.xlsx?sequence=1"
tmp = tempfile(fileext = ".xlsx")
download.file(url = url, destfile = tmp)
metadata<-read_excel(path=tmp,sheet="metadata",skip=12,col_names=F)
names(metadata)<-c("Col1","Col2")
veg_data <-readWorksheetFromFile(file = tmp, sheet = "data.txt")
veg_data<-veg_data[,11:123]
veg_data<-round(veg_data,digits = 2)
env_data<-read_excel(path = tmp, sheet = "data.txt")
env_data<-env_data[,1:4]
These list of commands will give the following: Metadata, Veg data, and Env data.

Metadata contains two columns, Col1 contains short codes used by the authors as surrogates of the full scientific names of species for the species which are stored in the Col2 column.

Veg data contains a site's species table of biomass values.

Env data contains a list of experimental variables.

species_names<-final_dataframe$acceptedname
my_traits<-c("h_max","le_area","leaf_mass","li_form_B","strategy")
retrieved_traits<-tr8(species_list = species_names,download_list = my_traits)
Maximum height is available in Ecoflora and its short code is h_max.

Leaf area is available in Ecoflora and its short code is le_area.

Leaf mass is available in LEDA and its short code is leaf_mass.

Life form is available in BiolFlor3 and its short code is li_form_B.

Originr Package: Used for invasive species: If we want to explore if the species listed in the data COULD be considered invasive.

install.packages("originr")   ---   How to install a package into RStudio
install_github("roponsci/originr")  ---  Installs GitHub for pushing analysis
library("originr")   --- Downloads the specific package required for analysis

eol(name='Pinus', dataset='gisd')
# Searched Name: Pinus   ---   Species Name
# Dataset Used: Global Invasive Species Database
# Website Used: eol

sp <- c("Pinus", "Prunus Campanulata Maxim")  --- Species names are the input
gisd(sp)   --- Loads the dataset, analyzes the dataset to find the specific species and its details
echo  "1st_column%2nd_column%3rd_column..4th_column" > Tr8_Plants_Data.txt
sed 's/%/\t/g' Tr8_Plants_Data.txt 
