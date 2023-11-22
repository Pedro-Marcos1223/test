SELECT 
    CONCAT(
        SUBSTRING_INDEX(nm_descricao, 'Total reclamações', 1),
        ' ',
        SUBSTRING_INDEX(SUBSTRING_INDEX(nm_descricao, 'Total reclamações:', -1), 'Data do evento:', 1),
        ' ',
        SUBSTRING_INDEX(SUBSTRING_INDEX(nm_descricao, 'Data do evento:', -1), 'Impacto:', 1),
        ' ',
        SUBSTRING_INDEX(SUBSTRING_INDEX(nm_descricao, 'Impacto:', -1), 'Classe ofenssora:', 1),
        ' ',
        SUBSTRING_INDEX(SUBSTRING_INDEX(nm_descricao, 'Classe ofenssora:', -1), 'Time resp:', 1),
        ' ',
        SUBSTRING_INDEX(SUBSTRING_INDEX(nm_descricao, 'Time resp:', -1), 'Incidentes:', 1),
        ' ',
        SUBSTRING_INDEX(SUBSTRING_INDEX(nm_descricao, 'Incidentes:', -1), 'Total reclamações:', -1)
    ) AS nm_descricao_calculado
FROM 
    sua_tabela;
