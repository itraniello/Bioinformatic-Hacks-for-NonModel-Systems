# Bioinformatic-Hacks-for-NonModel-Systems

Due to some issues with this notebook accessing NCBI, I created the BSgenome package on my personal machine with this command:
>forgeBSgenomeDataPkgFromNCBI(assembly_accession="GCF_000188095.3",
                            pkg_maintainer="Ian Traniello <it4770@princeton.edu>",
                             organism="Bombus impatiens")

Next, I ran:
>devtools::build("./BSgenome.Bimpatiens.NCBI.BIMP2.2/")
>devtools::check_built("BSgenome.Ainfernus.NCBI.ASM972954v1_1.0.0.tar.gz")
>devtools::install_local("BSgenome.Ainfernus.NCBI.ASM972954v1_1.0.0.tar.gz")

And this final output was moved to my R libraries directory on the HPC environment I'm using.


genomeAnnotation <- 
  createGenomeAnnotation(genome = BSgenome.Bimpatiens.NCBI.BIMP2.2)

bimp_txdb <- makeTxDbFromGFF(
  file = "/Genomics/kocherlab/itraniello/2023_BIMP_multiome_pilot/multiome/src/reference_genome/bimp2.2_filtered_ensembl_final.gtf",
  format = "gtf",
  dataSource = "NCBI", 
  organism = "Bombus impatiens",
  taxonomyId = 132113)

Same issue with internet, running this on my local machine.

library("AnnotationForge")
makeOrgPackageFromNCBI(version = "0.1",
                       author = "Ian Traniello <it4770@princeton.edu>",
                       maintainer = "Ian Traniello <it4770@princeton.edu>",
                       outputDir = ".",
                       tax_id = "132113",
                       genus = "Bombus",
                       species = "impatiens")
                       
install.packages("./", repos=NULL)
