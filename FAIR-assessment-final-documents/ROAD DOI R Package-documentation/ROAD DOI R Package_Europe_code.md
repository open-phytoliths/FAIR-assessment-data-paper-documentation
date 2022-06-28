#Load library roadoi
library(roadoi)

#Load file containing DOIs
dois_list<-read.table("DOIs_Europe.csv", sep=",", header=FALSE)

#Obtain open access information by calling function oadoi_fetch
result<-oadoi_fetch(dois=as.character(dois_list[,1]), email="open.phytoliths@gmail.com")

#Export results as CSV files
write.csv(result[,c(1,5:20)], "Open_access_status_Europe.csv")
write.csv(result$oa_locations[[1]], "Repositories_Europe.csv")
