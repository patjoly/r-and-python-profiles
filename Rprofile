local({r <- getOption("repos")
      r["CRAN"] <- "https://mirror.csclub.uwaterloo.ca/CRAN/"
      options(repos=r)})

q <- function (save="no", ...) {
  quit(save=save, ...)
}

# .First <- function(){
#  nothing for now
#}

.initial_wd <- getwd()

.Last <- function(){
  if(interactive()){

    hist_file = ''
    initial_wd_hist_file = file.path( .initial_wd, '.Rhistory' )
    # if R finds a history file there, that's the one that will 
    # have been loaded and that we want to save to

    if (file.exists( initial_wd_hist_file )) {
      hist_file <- initial_wd_hist_file
    } else {
      hist_file <- Sys.getenv("R_HISTFILE")
    }

    if(hist_file=="") {           # if it's still not defined, then in ~
      hist_file <- "~/.Rhistory"
    }
    savehistory(hist_file)
  }
}

auto.loads <-c("dplyr", "ggplot2")

attach(
  list(
    '%!in%' =  Negate('%in%'),
    '%wo%'  =  function(x, y) { x[!x %in% y] }
    ),
  name = "MyFunctions"
  )

# .env <- new.env()
# attach(.env)

# .env$unfactor <- function(df){
#   id <- sapply(df, is.factor)
#   df[id] <- lapply(df[id], as.character)
#   df
# }

message("Successfully loaded .Rprofile")
