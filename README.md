# patient-info
SELECT p.name AS "Patient",
       y.name AS "Physician",
       n.name AS "Nurse",
       s.end_time AS "Date of Release",
       pr.name AS "Treatment going on",
       r.roomnumber AS "Room",
       r.blockfloor AS "Floor",
       r.blockcode AS "Block"
 FROM undergoes u
 JOIN patient p ON u.patient=p.ssn
 JOIN physician y ON u.physician=y.employeeid
 LEFT JOIN nurse n ON u.assistingnurse=n.employeeid
 JOIN stay sON u.patient=s.patient
 JOIN room r ON s.room=r.roomnumber
 JOIN procedure pr ON u.procedure=pr.code;
