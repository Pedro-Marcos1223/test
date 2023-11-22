SELECT 
    CONCAT(
        CASE WHEN CHARINDEX('Total reclamações', nm_descricao) > 0 THEN LEFT(nm_descricao, CHARINDEX('Total reclamações', nm_descricao) - 1) ELSE '' END,
        ' ',
        CASE WHEN CHARINDEX('Total reclamações:', nm_descricao) > 0 AND CHARINDEX('Data do evento:', nm_descricao) > 0 THEN SUBSTRING(nm_descricao, 
                   CHARINDEX('Total reclamações:', nm_descricao) + LEN('Total reclamações:'), 
                   CHARINDEX('Data do evento:', nm_descricao) - CHARINDEX('Total reclamações:', nm_descricao) - LEN('Total reclamações:')
                  ) ELSE '' END,
        ' ',
        CASE WHEN CHARINDEX('Data do evento:', nm_descricao) > 0 AND CHARINDEX('Impacto:', nm_descricao) > 0 THEN SUBSTRING(nm_descricao, 
                   CHARINDEX('Data do evento:', nm_descricao) + LEN('Data do evento:'), 
                   CHARINDEX('Impacto:', nm_descricao) - CHARINDEX('Data do evento:', nm_descricao) - LEN('Data do evento:')
                  ) ELSE '' END,
        ' ',
        CASE WHEN CHARINDEX('Impacto:', nm_descricao) > 0 AND CHARINDEX('Classe ofenssora:', nm_descricao) > 0 THEN SUBSTRING(nm_descricao, 
                   CHARINDEX('Impacto:', nm_descricao) + LEN('Impacto:'), 
                   CHARINDEX('Classe ofenssora:', nm_descricao) - CHARINDEX('Impacto:', nm_descricao) - LEN('Impacto:')
                  ) ELSE '' END,
        ' ',
        CASE WHEN CHARINDEX('Classe ofenssora:', nm_descricao) > 0 AND CHARINDEX('Time resp:', nm_descricao) > 0 THEN SUBSTRING(nm_descricao, 
                   CHARINDEX('Classe ofenssora:', nm_descricao) + LEN('Classe ofenssora:'), 
                   CHARINDEX('Time resp:', nm_descricao) - CHARINDEX('Classe ofenssora:', nm_descricao) - LEN('Classe ofenssora:')
                  ) ELSE '' END,
        ' ',
        CASE WHEN CHARINDEX('Time resp:', nm_descricao) > 0 AND CHARINDEX('Incidentes:', nm_descricao) > 0 THEN SUBSTRING(nm_descricao, 
                   CHARINDEX('Time resp:', nm_descricao) + LEN('Time resp:'), 
                   CHARINDEX('Incidentes:', nm_descricao) - CHARINDEX('Time resp:', nm_descricao) - LEN('Time resp:')
                  ) ELSE '' END,
        ' ',
        CASE WHEN CHARINDEX('Incidentes:', nm_descricao) > 0 THEN RIGHT(nm_descricao, LEN(nm_descricao) - CHARINDEX('Incidentes:', nm_descricao) + 1) ELSE '' END
    ) AS nm_descricao_calculado
FROM 
    sua_tabela;
