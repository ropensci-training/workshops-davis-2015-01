Thus far, we have focused on accessing large aggregations of data assembled by professional data curation services and made available over a web interface or API.  Now we turn our attention to the rest of the data.

Such centrally curated data sources are examples of _vertically integrated repositories_: they provide a fixed number of variables, adding new data as rows like a Tetris game.  Before most research data can be entered into these aggregations, all other details that don't fit neatly into the table must be stripped out; thus much essential information is lost. 

Metadata-driven repositories offer an alternative approach to vertical integration.  Instead of removing data that doesn't fit, this approach adds additional annotations that permit computers to interpret and extract meaningful common features while leaving the original data intact.  

In this section, we introduce R packages that facilitate this annotation and submission of heterogeneous data to such repositories.  
