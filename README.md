# Significant verschil tussen genexpressie van mensen met reumatoïde artritis en gezonde mensen
<sub>Niels Hoitsma - nielshoitsma1@student.nhlstenden.com - laatste bewerking: 29-5-2026</sub>
## Inleiding
Reumatoïde artritis (RA) is een chronische ziekte waarbij het immuunsysteem het synovium (ook wel bekend als het gewrichtsslijmvlies) van een mens als het ware aanvalt. Hierdoor kan ontsteking van gewrichtsslijmvlies ontstaan, afbraak van kraakbeen plaatsvinden en vorming van abnormaal weefsel, ook wel pannus genoemd [[1]](https://pmc.ncbi.nlm.nih.gov/articles/PMC8780115/pdf/ijms-23-00905.pdf). Hierdoor kunnen patienten last krijgen van pijn, zwellingen, of stijfheid. Belangrijke oorzaken van RA zijn erfelijkheid, omgevingsfactoren zoals roken, en immuunactivatie. Momenteel is er helaas nog geen goed werkend medicijn. Er zijn verschillende medicijnen beschikbaar, maar niet alle patienten reageren daar goed op. Door het gebrek aan een goed werkend medicijn is er behoefte naar onderzoek naar reuma [[2]](https://core.ac.uk/reader/77600864?utm_source=linkout).
### Onderzoeksdoel
In dit onderzoek wordt met behulp van transcriptomics onderzocht welke genen tot expressie komen bij vier mensen met RA en vier mensen zonder RA. De acht verkregen samples worden met het humane genoom vergeleken in Rstudio, waarbij onderzoek gedaan wordt naar de genexpressie en metabolic pathways.
## Materiaal en Methode
Om te kunnen onderzoeken welke genen meer tot expressie komen bij mensen die ziek zijn met reuma dan bij mensen die gezond zijn worden de data geanalyseerd van 4 gezonde mensen, en 4 mensen die besmet zijn met reuma. De data is afkomstig vanuit het synoviumbiopt: weefsel afkomstig in gewrichtsslijmvlies. Personen met RA zijn positief getest op ACPA, personen zonder RA negatief. Van de zieke mensen is het minimaal twaalf maanden bekend dat de mensen ziek zien met RA. De gebruikte data is te vinden onder ["Data>RawData"](https://github.com/NielsHoi/26-5-Casus_Transcriptomics-/tree/main/Data/RawData). 

De data is uitgelijnd tegen het [referentiegenoom GRCh38.p14](https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_000001405.40/) in Rstudio (Versie 2026.01.0+392) met behulp van Rsubread (Versie 2.24.0) om vervolgens voor elke sample [BAM-files](https://github.com/NielsHoi/26-5-Casus_Transcriptomics-/tree/main/Data/ProcessedData) te maken. Vervolgens wordt met de verkregen data een [count matrix](https://github.com/NielsHoi/26-5-Casus_Transcriptomics-/tree/main/Data/ProcessedData) gemaakt.

Nadat de count matrix gemaakt is, kan vervolgens een statistische analyse gedaan worden met behulp van pakket DESeq2 (Versie 1.50.2) waarbij de genexpressie van de mensen met RA vergeleken kan worden met de gezonde mensen, hierbij worden genen met een P-waarde lager dan 0,05 beschouwd als statistisch significant verschillend. De genexpressie van verschillende genen kan dan worden uitgebeeld in een volcanoplot met behulp van de functie EnhancedVolcano (Versie 1.28.2).

Vervolgens wordt een gene ontology-analyse (GO-analyse) en een KEGG-pathway-analyse om zicht te krijgen op welke genen belangrijk zijn in verrschillende metabolic pathways. Het volledige script wat gebruikt wordt in Rstudio is te vinden bij ["Script"](https://github.com/NielsHoi/26-5-Casus_Transcriptomics-/tree/main/Script).

C:\Users\niels\OneDrive - NHL Stenden\Downloads\flowchart.png
## Resultaten
Om te zien welke genen tot expressie komen bij reumatoïde artrits is een volcano plot gemaakt, de gemaakte volcanoplot is te vinden bij ["Resultaten>VolcanoplotReuma.png"](https://github.com/NielsHoi/26-5-Casus_Transcriptomics-/blob/main/Resultaten/VolcanoplotReuma.png). In de volcanplot is op de x-as de log2 waarde van de fold-change te zien, en op de y-as de -log10 P-waarde. De groene stippen zijn genen die niet statistisch significant zijn. De grijze stippen zijn genen waarbij er geen verschil is gevonden tussen de genexpressie bij mensen met RA en gezonde mensen. De rode stippen zijn genen die statistisch significant verschillen in genexpressie. In de volcanoplot is te zien dat het gen ANKRD30BL het meest statistisch significant is. 

Verder is ook een GO-analyse gedaan. De GO-analyse is terug te vinden bij ["Resultaten>GOplot.png"](https://github.com/NielsHoi/26-5-Casus_Transcriptomics-/blob/main/Resultaten/GO_plot.png). Op de y-as van de GO-plot staan verschillende biologische processen, en op de x-as hoeveel genen bij het bijbehorende biologische proces hoort. De kleur van de stippen laat zien hoe statisch significant de waarden zijn, waarbij rood sterk significant, en blauw minder significant. In de plot is te zien dat lymphocyte differentiation veel genen heeft die ook belangrijk zijn bij RA. 

Daarnaast is een KEGG-analyse uitgevoerd. De KEGG-analyse is te vinden bij [Resultaten>keggpathway_plot.png](https://github.com/NielsHoi/26-5-Casus_Transcriptomics-/blob/main/Resultaten/keggpathway_plot.png). Hierin zijn op de y-as verschillende metabolic pathways zichtbaar. Op de x-as is het percentage genen dat overlap heeft tussen de pathway en het onderzoek. 

Verder is er nog een pathway geanalyseerd, de [Rheumatoid arthritis pathway](https://www.kegg.jp/entry/map05323). De geanalyseerde pathway is te vinden ["Resultaten
/RA_Pathway.png"](https://github.com/NielsHoi/26-5-Casus_Transcriptomics-/blob/main/Resultaten/RA_Pathway.png). Op deze kaart zijn verschillende genen te zien die belangrijk zijn voor mensen die ziek zijn met RA. Op de geanalyseerde kaart zijn sommige genen gekleurd. Als het gen rood is gekleurd is de expressie hoog, en bij een gen dat blauw is gekleurd, wordt de expressie juist lager.

## Conclusie
Bij dit onderzoek werd gekeken naar de genexpressie van genen die betrokken zijn bij Reumatoïde arrtritis (RA). Uit dit onderzoek blijkt dat er statistisch significant verschil zit tussen de genexpressie van mensen die ziek zijn met RA, en gezonde mensen. De GO-analyse laat zien dat genen die meer tot expressie komen bij mensen met RA betrokken zijn bij het differentieren van lymfocyten en andere immuunsysteem gerelateerde biologische processen. De resultaten bevestigen dat reumaroïde artritis een autoimmuunziekte is. Daarnaast is er bij de pathway-analyse te zien dat er ook sprake is van ontstekingen en abnormale groei van pannus (weefsel in gewrichten).  

## Bronnen en AI-gebruik
### Bronnen
Voor het verslag zijn de volgende bronnen gebruikt:
[[1]](https://pmc.ncbi.nlm.nih.gov/articles/PMC8780115/pdf/ijms-23-00905.pdf) Jang, S., Kwon, E. J., & Lee, J. J. (2022) Rheumatoid Arthritis: Pathogenic Roles of Diverse Immune Cells. In International Journal of Molecular Sciences (Vol. 23, Number 2). MDPI. https://doi.org/10.3390/ijms23020905

[[2]](https://core.ac.uk/reader/77600864?utm_source=linkout) Author, C., Smolen, J. S., Author, F., Smolen Order of Authors, J. S., Aletaha, D., McInnes, I., & Smolen, J. (n.d.). Elsevier Editorial System(tm) for The Lancet Manuscript Draft Manuscript Number: Title: Rheumatoid Arthritis Article Type: Invited Seminar Seminar: Rheumatoid Arthritis.
### AI-gebruik
AI is gebruikt om te helpen met spelling, het helpen beginnen met informatie opzoeken, en met het uitleggen van errors in Rstudio.
