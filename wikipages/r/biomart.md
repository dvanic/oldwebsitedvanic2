---
layout: default
title: biomaRt
---
## General template

    library(biomaRt)

	# To use the latest version of biomart
	# mart <- useMart(biomart="ENSEMBL_MART_ENSEMBL", host="www.ensembl.org", path="/biomart/martservice")
	ensembl=useMart("ensembl")
	ensembl = useDataset("hsapiens_gene_ensembl",mart=ensembl)
	IDs <- c("","","")
	# listAttributes(ensembl)[1:50,]
	ID <- getBM(attributes=c("ensembl_gene_id","hgnc_symbol"), filters = "hgnc_symbol", values=IDs, mart=ensembl)

Convert between species

Example: get human gene names from mouse transcript names
	
	ensembl=useMart("ensembl")
	human = useMart("ensembl", dataset = "hsapiens_gene_ensembl")
	mouse = useMart("ensembl", dataset = "mmusculus_gene_ensembl")
	a<-getLDS(attributes = c("ensembl_transcript_id"), filters = "ensembl_transcript_id", values = a=data$TranscriptID,mart = mouse, attributesL = c("ensembl_gene_id"), martL = human)

Archive version of ensembl

    ensembl=useMart(host="jun2013.archive.ensembl.org", biomart="ENSEMBL_MART_ENSEMBL", dataset = "hsapiens_gene_ensembl")