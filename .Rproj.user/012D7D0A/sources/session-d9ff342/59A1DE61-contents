load(url(("https://github.com/cursos-metodos-facso/metod1-MCS/raw/main/resource/files/ELSOC_W05_v1.0_R.RData")))
pacman::p_load(dplyr, # Manipulacion datos
               sjmisc, # Descriptivos
               sjPlot, # Tablas
               sjlabelled, #etiquetas
               kableExtra, #Tablas
               GGally, # Correlaciones
               corrplot) # Correlaciones

options(scipen = 999) # para desactivar notacion cientifica
proc_elsoc <- elsoc_2021 %>% select(edad=m0_edad, ingreso=m13, educacion=m01, desigualdad=c18_11, esfuerzo=c18_09, inteligencia=c18_10)
sjmisc::descr(proc_elsoc,
              show = c("label","range", "mean", "sd", "NA.prc", "n")) %>%
  kable(.,"markdown")
names(proc_elsoc)
proc_elsoc <- proc_elsoc %>% set_na(., na = c(-999, -888, -777, -666))

frq(proc_elsoc$esfuerzo)
proc_elsoc_original <- proc_elsoc
dim(proc_elsoc)
M <- cor(proc_elsoc_original, use = "complete.obs")
M
sjPlot::tab_corr(proc_elsoc_original, 
                 triangle = "lower")
sjPlot::tab_corr(proc_elsoc_original, 
                 na.deletion = "pairwise", # espeficicamos tratamiento NA
                 triangle = "lower")