SELECT 
    CONCAT(
        CAST(SUM(Nu_tempo_exposto_seg) / 3600 AS INT), 'h', 
        IIF(CAST(SUM(Nu_tempo_exposto_seg) % 3600 / 60 AS INT) < 10, '0', ''),
        CAST(SUM(Nu_tempo_exposto_seg) % 3600 / 60 AS INT)
    ) AS 'Tempo exposto horas'
FROM 
    SuaTabela
