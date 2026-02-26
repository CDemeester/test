# Utility functions ------------------------------------------------------
safe_cli_warn <- function(message) {
  # if cli package is available
  if (requireNamespace("cli", quietly = TRUE)) {
    cli::cli_warn(message)
  } else {
    warning(paste(message, collapse = "\n"), call.=FALSE)
  }
}

safe_cli_inform <- function(message) {
  # if cli package is available
  if (requireNamespace("cli", quietly = TRUE)) {
    cli::cli_inform(message)
  } else {
    message(paste(message, collapse = "\n"), call.=FALSE)
  }
}


# Check Renv Initialization -----------------------------------------------

tryCatch(
  {
    renv_initialized <<- TRUE
    source("renv/activate.R")
  },
  warning = function(e) {
    renv_initialized <<- FALSE
  }
)



# Check Renv status -----------------------------------------------------------

if(renv_initialized){
  renv_status <- renv::status()

  renv_syncronized <- renv_status$synchronized
  if(!renv_syncronized){
    safe_cli_warn(c(
      "!" = "R environment is not in sync with specifications (renv.lock file).",
      ">" = "If this is the first time opening this project, run {.run renv::restore()} to install packages",
      ">" = "Otherwise, you can run {.run renv::snapshot()} to update the lockfile."
    )
  )
  }
}


# Is ESQlabsR Project Initialized ? ---------------------------------------
if (renv_initialized && renv_syncronized) {
  ## List files
  project_files <- list.files(".")

  ## Look for ProjectConfiguration.xlsx
  initialized_project <- "ProjectConfiguration.xlsx" %in% project_files

  if (!initialized_project) {
    safe_cli_warn(c(
      "!" = "ESQlabsR project not initialized.",
      ">" = "Please run {.run esqlabsR::initProject()} to initialize the project."
    )
    )
  }
}


# SharePoint Setup --------------------------------------------------------
if (renv_initialized && renv_syncronized && initialized_project) {
  # Look for string that looks like environment variables in Project COnfiguration
  # Environment variables are capital case and underscore separated
  used_env_vars <- unique(grep(
    "^[A-Z_]+$",
    unlist(strsplit(
      x = readxl::read_excel("ProjectConfiguration.xlsx")$Value,
      "/"
    )),
    value = TRUE
  ))
  # Get missing environment variables
  missing_env_vars <- used_env_vars[Sys.getenv(used_env_vars) == ""]

  if (length(missing_env_vars) > 0) {
    # Load environment variables
    safe_cli_inform(c(
      "i" = "ProjectConfiguration.xslx seems to contain environment variables. However, their values are not set.",
      ">" = "Open .Renviron file using {.run usethis::edit_r_environ('project')}, append the following environment variables and add their values:"
    ))
    safe_cli_inform(paste0(missing_env_vars, "="))
  }
}


# Clean environment -------------------------------------------------------
## Remove all environment variables
rm(list = ls())
