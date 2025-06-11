local({r <- getOption("repos")
      r['CRAN'] <- 'https://mirror.csclub.uwaterloo.ca/CRAN/'
      options(repos=r)})

q <- function (save="no", ...) {
  quit(save=save, ...)
}

.First <- function(){
  if(interactive()){

    hist_file = ''
    initial_wd_hist_file = file.path( .initial_wd, '.Rhistory' )

    if ( file.exists( initial_wd_hist_file ) ) {
      hist_file <- initial_wd_hist_file
    } else {
      hist_file <- Sys.getenv( 'R_HISTFILE' )
      if ( hist_file=='' ) hist_file <- "~/.Rhistory"
    }

    cat( "\nReading history from:\n\t", hist_file, "\n\n" )
    utils::loadhistory(hist_file)
  }
}

.initial_wd <- getwd()

.Last <- function(){
  if(interactive()){

    hist_file = ''
    initial_wd_hist_file = file.path( .initial_wd, '.Rhistory' )

    if ( file.exists( initial_wd_hist_file ) ) {
      hist_file <- initial_wd_hist_file
    } else {
      hist_file <- Sys.getenv( 'R_HISTFILE' )
      if ( hist_file=='' ) hist_file <- "~/.Rhistory"
    }

    savehistory(hist_file)
  }
}

# packages to load at startup

no_warning_at_start <- function( a_package ){
  suppressWarnings( suppressPackageStartupMessages(
    library( a_package, character.only=TRUE )) )
}
load_at_start <- c("dplyr", "ggplot2")

if (interactive()) {
  invisible( sapply( load_at_start, no_warning_at_start ) )
}

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

rm( list = ls(pattern = '_at_start$') )

message("Successfully loaded .Rprofile")
