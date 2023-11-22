SELECT 
    CONCAT(
        LEFT(nm_descricao, CHARINDEX('Total reclamações', nm_descricao) - 1),
        ' ',
        SUBSTRING(nm_descricao, 
                   CHARINDEX('Total reclamações:', nm_descricao) + LEN('Total reclamações:'), 
                   CHARINDEX('Data do evento:', nm_descricao) - CHARINDEX('Total reclamações:', nm_descricao) - LEN('Total reclamações:')
                  ),
        ' ',
        SUBSTRING(nm_descricao, 
                   CHARINDEX('Data do evento:', nm_descricao) + LEN('Data do evento:'), 
                   CHARINDEX('Impacto:', nm_descricao) - CHARINDEX('Data do evento:', nm_descricao) - LEN('Data do evento:')
                  ),
        ' ',
        SUBSTRING(nm_descricao, 
                   CHARINDEX('Impacto:', nm_descricao) + LEN('Impacto:'), 
                   CHARINDEX('Classe ofenssora:', nm_descricao) - CHARINDEX('Impacto:', nm_descricao) - LEN('Impacto:')
                  ),
        ' ',
        SUBSTRING(nm_descricao, 
                   CHARINDEX('Classe ofenssora:', nm_descricao) + LEN('Classe ofenssora:'), 
                   CHARINDEX('Time resp:', nm_descricao) - CHARINDEX('Classe ofenssora:', nm_descricao) - LEN('Classe ofenssora:')
                  ),
        ' ',
        SUBSTRING(nm_descricao, 
                   CHARINDEX('Time resp:', nm_descricao) + LEN('Time resp:'), 
                   CHARINDEX('Incidentes:', nm_descricao) - CHARINDEX('Time resp:', nm_descricao) - LEN('Time resp:')
                  ),
        ' ',
        RIGHT(nm_descricao, LEN(nm_descricao) - CHARINDEX('Incidentes:', nm_descricao) + 1)
    ) AS nm_descricao_calculado
FROM 
    sua_tabela;
