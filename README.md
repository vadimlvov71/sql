select last_foto.foto_id, count_foto.count_pos, last_foto.rubrica,last_foto.foto
from
(select max(foto_id) as foto_id, foto,rubrica from table group by rubrica) as last_foto,
(select count(*) as count_pos, rubrica from table group by rubrica) as count_foto
where last_foto.rubrica=count_foto.rubrica



select table1.closedate AS "time", DATE_FORMAT(table1.closedate,'%Y%m') AS metric, table1.count1, table2.count2
from
(select COUNT(table1.id) as count1, table1.date, table1.closedate from glpi_tickets as table1 where users_id_lastupdater = 12535 AND status = 6 GROUP BY DATE_FORMAT(closedate,'%Y%m') ORDER BY closedate ASC) as table1,
(select IFNULL(COUNT(table2.id), 0) as count2, table2.date from glpi_tickets  as table2 where users_id_lastupdater = 12535 AND status <> 6 GROUP BY DATE_FORMAT(date,'%Y%m') ORDER BY date ASC) as table2
WHERE DATE_FORMAT(table1.closedate,'%Y%m') = DATE_FORMAT(table2.date,'%Y%m')
если в правой таблице ноль значения, делаем LEFT JOIN:

select table1.closedate AS "time", DATE_FORMAT(table1.closedate,'%Y%m') AS metric, table1.count1, table2.count2
from
(select COUNT(table1.id) as count1, table1.date, table1.closedate from glpi_tickets as table1 where users_id_lastupdater = 12535 AND status = 6 GROUP BY DATE_FORMAT(closedate,'%Y%m') ORDER BY closedate ASC) as table1
LEFT JOIN
(select IFNULL(COUNT(table2.id), 0) as count2, table2.date from glpi_tickets  as table2 where users_id_lastupdater = 12535 AND status <> 6 GROUP BY DATE_FORMAT(date,'%Y%m') ORDER BY date ASC) as table2
ON DATE_FORMAT(table1.closedate,'%Y%m') = DATE_FORMAT(table2.date,'%Y%m')
