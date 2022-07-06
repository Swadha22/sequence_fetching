## sequence_fetching

### To fetch Blast sequences

    import pandas as pd
    arry = []
    filenames=[]
    with open ("/home/roylab/swadha/Diploscapter/NEMATODE/2_filtered/H2A/All_H2A.txt", "r") as f:
        #with open ("fetched_sequences.txt", "w") as g:
            for line in f:
                arry = line.split("\t")
                #print (arry[1])
                l = len(arry)
                #print(l)
                with open (arry[0],"r") as spFile:
                    #allLines = splLines in spFile
                    takeNextLine = 0
                    for spLines in spFile:
                        if (takeNextLine == 1):
                            print(">" + arry[2] + "#" + arry[1] + "#" + arry[0])
                            print(spLines)
                            takeNextLine = 0

                        if (arry[2] in spLines):
                            takeNextLine = 1
                            #print(spLines)


### To fetch intron-exon sequences

      import pandas as pd
      arry = []
      filenames=[]
      with open ("output.txt", "w") as f:
          with open ("/home/roylab/swadha/phylogeny/nematodes_V2/step1_intron_exons/fetch_sequences_inputFile.csv", "r") as g:
              for inputLine in g:
                  arryInput = inputLine.split(",")
                  with open (arryInput[2], "r") as h:
                      takeNextLine = False
                      for line in h:
                          if (takeNextLine == True):
                              print(line)
                              takeNextLine = False

                          if (arryInput[1] in line):
                              outputLine = arryInput[1]
                              for i in range(len(arryInput)):
                                  if (i >= 2 and arryInput[i] != ""):
                                      outputLine = outputLine + "\t" + arryInput[i]
                              takeNextLine = True
                              print(outputLine)
                              
                              
                              
