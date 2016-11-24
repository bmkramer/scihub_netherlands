# Dissemin API - R script

My first R script - please be kind :-) 

##Description
This script uses the Dissemin API to get information on online availability (gold and green Open Access) of academic articles, identified by their DOI, as well as publisher policies on archiving. 

[Dissemin API documentation] (http://dev.dissem.in/api.html)
 
[Dissemin documentation] (https://media.readthedocs.org/pdf/dissemin/latest/dissemin.pdf)

##Input / output
This script uses as input a csv file with a list of doi's in a column labeled "DOI"

The output is a dataframe (written to a csv file) with, for each DOI, the following information from the Dissemin API:
  - original DOI that was used as input
  - classification = self-archiving policy of the publisher: 
    - "OA" (available from the publisher) 
    - "OK" (some version can be shared)
    - "UNK" (unknown/unclear sharing policy)
    - "NOK" (restrictive sharing policy).
  - publisher
  - journal title
  - issn
  - journal policy on sharing preprint version
  - journal policy on sharing postprint version
  - journal policy on sharing publisher version
  - date of publication
  - URL where freely available version can be found, if any. 

##Caveats / issues
  - The script uses loops (bad R!), if someone can improve this using an apply-function, please do! 
  - The script currently stops executing when it encounters a HTTP status 404 for one of the DOIs checked. 
    - This could probably be circumvented with try.catch(), but I don't know how (yet)
    - In the current setup, the script can be rerun manually, skipping the offending DOI by resetting the loop counter. 
    I'm sure there is a more elegant solution! 
    
  - For some DOis, results obstained through this script are empty while Dissemin API does return results - so will need a closer look at the Dissemin API output parameters. 

##The script
[DOI_queries_Dissemin_API.R](https://github.com/bmkramer/scihub_netherlands/blob/Dissemin_API_R/DOI_queries_Dissemin_API.R)
