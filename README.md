# sqlzoo-selected-solutions

Self Join Question 10 (https://sqlzoo.net/wiki/Self_join)

SELECT t2.num, t2.company, t1.name, t1.num, t1.company FROM
(SELECT DISTINCT stopc.name, c.num, c.company
FROM route c JOIN route d ON
  (c.company=d.company AND c.num=d.num)
  JOIN stops stopc ON (c.stop=stopc.id)
  JOIN stops stopd ON (d.stop=stopd.id)
WHERE stopd.name = 'Lochend') AS t1

JOIN

(SELECT DISTINCT stopb.name, b.num, b.company
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE stopa.name='Craiglockhart') AS t2

ON t1.name = t2.name

ORDER BY t2.num, t2.company, t1.name, t1.num, t1.company