ALTER TABLE `hos.roomno`
	ADD COLUMN `std_code` INT(6) NOT NULL DEFAULT '199100' AFTER `roomname2`,
	ADD COLUMN `spclty` VARCHAR(1) NOT NULL DEFAULT 'N' AFTER `std_code`;

ALTER TABLE `hos.hosbed` ADD COLUMN `std_bed` VARCHAR(2) NULL DEFAULT '00' AFTER `nouse`;

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET NAMES utf8 */;
/*!50503 SET NAMES utf8mb4 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;


-- Dumping database structure for his_connect
DROP DATABASE IF EXISTS `his_connect`;
CREATE DATABASE IF NOT EXISTS `his_connect` /*!40100 DEFAULT CHARACTER SET tis620 */;
USE `his_connect`;

-- Dumping structure for view his_connect.allergy
DROP VIEW IF EXISTS `allergy`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `allergy` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`drug_name` VARCHAR(1) NULL COMMENT 'ชื่อยาที่แพ้' COLLATE 'tis620_thai_ci',
	`symptom` TEXT NULL COMMENT 'หมายเหตุ' COLLATE 'tis620_thai_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.appointment
DROP VIEW IF EXISTS `appointment`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `appointment` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`seq` CHAR(0) NOT NULL COLLATE 'utf8mb4_general_ci',
	`date_serve` DATE NOT NULL,
	`time_serve` BINARY(0) NULL,
	`date` DATE NOT NULL,
	`time` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`department` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`detail` VARCHAR(1) NULL COLLATE 'tis620_thai_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.bedno
DROP VIEW IF EXISTS `bedno`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `bedno` (
	`bedno` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`bedtype` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`bedtype_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`roomno` CHAR(0) NOT NULL COLLATE 'utf8mb4_general_ci',
	`wardcode` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`wardname` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`std_code` INT(6) NULL,
	`bed_status_type_id` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci',
	`bed_status_type_name` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.chronic
DROP VIEW IF EXISTS `chronic`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `chronic` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`icd_code` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`icd_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`start_date` DATE NULL,
	`time_serve` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.diagnosis
DROP VIEW IF EXISTS `diagnosis`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `diagnosis` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`date` DATE NOT NULL,
	`time_serve` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`seq` SMALLINT(6) NOT NULL,
	`diag_type` CHAR(1) NULL COLLATE 'tis620_thai_ci',
	`icd_code` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`icd_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.diag_vwxy
DROP VIEW IF EXISTS `diag_vwxy`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `diag_vwxy` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`visitno` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`DATE` DATE NOT NULL,
	`diagcode` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`diag_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`diag_type` CHAR(1) NULL COLLATE 'tis620_thai_ci',
	`dr` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`episode` CHAR(0) NOT NULL COLLATE 'utf8mb4_general_ci',
	`codeset` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci',
	`d_update` DATE NULL
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.drug
DROP VIEW IF EXISTS `drug`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `drug` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`seq` INT(4) NOT NULL,
	`date_serve` DATE NOT NULL,
	`time_serve` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`drug_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`qty` SMALLINT(6) NOT NULL,
	`unit` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`usage_line1` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`usage_line2` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`usage_line3` VARCHAR(1) NULL COLLATE 'tis620_thai_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.hospital
DROP VIEW IF EXISTS `hospital`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `hospital` (
	`provider_code` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`provider_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.lab
DROP VIEW IF EXISTS `lab`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `lab` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`seq` INT(11) NOT NULL,
	`date_serve` DATE NOT NULL,
	`lab_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`lab_result` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`standard_result` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`time_serve` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`IOPD` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.person
DROP VIEW IF EXISTS `person`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `person` (
	`PatientID` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`title_code` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci',
	`fname` VARCHAR(1) NULL COLLATE 'utf8_general_ci',
	`lname` VARCHAR(1) NULL COLLATE 'utf8_general_ci',
	`CID` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`sex_code` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci',
	`birthdate` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci',
	`marry_status` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci',
	`nationality` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci',
	`citizenship` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci',
	`religion` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci',
	`addr` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`vill` CHAR(3) NULL COLLATE 'tis620_thai_ci',
	`addCode` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`Tel` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`last_update` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`occupation` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.procedure
DROP VIEW IF EXISTS `procedure`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `procedure` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`seq` INT(11) NOT NULL,
	`date_serve` DATE NOT NULL,
	`procedure_code` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`procedure_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`time_serve` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci',
	`start_date` DATE NOT NULL,
	`start_time` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci',
	`end_date` DATE NOT NULL,
	`end_time` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.profile
DROP VIEW IF EXISTS `profile`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `profile` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`cid` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`title_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`first_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`last_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.refer
DROP VIEW IF EXISTS `refer`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `refer` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`date_serve` DATE NOT NULL,
	`seq` SMALLINT(6) NOT NULL,
	`hcode_to` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`name_to` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`reason` TEXT NULL COLLATE 'tis620_thai_ci',
	`time_serve` VARCHAR(1) NULL COLLATE 'tis620_thai_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.sendward
DROP VIEW IF EXISTS `sendward`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `sendward` (
	`hospcode` VARCHAR(1) NOT NULL COLLATE 'utf8mb4_general_ci',
	`wardcode` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`new_case` DOUBLE NULL,
	`empty_bad` DOUBLE NULL,
	`discharge` DOUBLE NULL,
	`death` INT(1) NOT NULL
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.service
DROP VIEW IF EXISTS `service`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `service` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`seq` SMALLINT(6) NOT NULL,
	`date` DATE NOT NULL,
	`bp` SMALLINT(6) NULL,
	`bp1` SMALLINT(6) NULL,
	`puls` SMALLINT(6) NULL,
	`time_serve` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.vaccine
DROP VIEW IF EXISTS `vaccine`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `vaccine` (
	`hn` VARCHAR(1) NOT NULL COLLATE 'tis620_thai_ci',
	`date_serve` DATE NOT NULL,
	`time_serve` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`vaccine_code` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`vaccine_name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci'
) ENGINE=MyISAM;

-- Dumping structure for view his_connect.ward
DROP VIEW IF EXISTS `ward`;
-- Creating temporary table to overcome VIEW dependency errors
CREATE TABLE `ward` (
	`ward` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`name` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`spclty` VARCHAR(1) NULL COLLATE 'tis620_thai_ci',
	`sss_code` VARCHAR(1) NULL COLLATE 'utf8mb4_general_ci',
	`bedcount` BIGINT(21) NOT NULL,
	`bedspecial` INT(1) NULL
) ENGINE=MyISAM;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `allergy`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `allergy` AS select `pt`.`ptallergy`.`hn` AS `hn`,`pt`.`ptallergy`.`listname` AS `drug_name`,`pt`.`ptallergy`.`descrip` AS `symptom` from `pt`.`ptallergy`
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `appointment`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `appointment` AS select `p`.`hn` AS `hn`,'' AS `seq`,`p`.`regdate` AS `date_serve`,NULL AS `time_serve`,`p`.`appointdate` AS `date`,`p`.`timeappoint` AS `time`,(select `r`.`roomname` from `hos`.`roomno` `r` where (`r`.`roomcode` = `p`.`toroomappoint`)) AS `department`,`p`.`causeappoint` AS `detail` from `pt`.`ptappoint` `p` order by `p`.`regdate` desc limit 500
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `bedno`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `bedno` AS select `b`.`bed` AS `bedno`,`b`.`bed_type` AS `bedtype`,`hh`.`name` AS `bedtype_name`,`cc`.`roomname` AS `name`,'' AS `roomno`,`b`.`now_ward` AS `wardcode`,`cc`.`roomname` AS `wardname`,`cc`.`std_code` AS `std_code`,'1' AS `bed_status_type_id`,'use' AS `bed_status_type_name` from (((`hos`.`hosbed` `a` left join `ipd`.`ipd` `b` on(((`b`.`bed` = `a`.`code`) and (`b`.`bed_type` = `a`.`bedtype`)))) left join `hos`.`roomno` `cc` on((`cc`.`roomcode` = `b`.`now_ward`))) left join `hos`.`codeinhos` `hh` on((`hh`.`code` = `b`.`bed_type`))) where (`b`.`datedsc` = '0000-00-00')
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `chronic`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `chronic` AS select `c`.`hn` AS `hn`,`c`.`icd10` AS `icd_code`,(select `i`.`description` from `hos`.`icd101_4` `i` where (`i`.`code` = `c`.`icd10`) limit 1) AS `icd_name`,`c`.`dateadm` AS `start_date`,'00:00:00' AS `time_serve` from `pt`.`ptclinic` `c` where ((`c`.`datedsc` = '0000-00-00') and (`c`.`icd10` is not null) and (`c`.`icd10` <> ''))
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `diagnosis`;
CREATE ALGORITHM=UNDEFINED SQL SECURITY DEFINER VIEW `diagnosis` AS select `o`.`hn` AS `hn`,`o`.`regdate` AS `date`,`o`.`timestart` AS `time_serve`,`o`.`frequency` AS `seq`,`d`.`dxtype` AS `diag_type`,`d`.`diag` AS `icd_code`,`d`.`descrip` AS `icd_name` from (`opd`.`opd` `o` join `opd`.`odiag` `d` on(((`d`.`regdate` = `o`.`regdate`) and (`o`.`hn` = `d`.`hn`) and (`d`.`frequency` = `o`.`frequency`)))) order by `o`.`regdate` desc
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `diag_vwxy`;
CREATE ALGORITHM=UNDEFINED SQL SECURITY DEFINER VIEW `diag_vwxy` AS select `a`.`hn` AS `hn`,`a`.`docno` AS `visitno`,`a`.`regdate` AS `DATE`,`b`.`diag` AS `diagcode`,`b`.`descrip` AS `diag_name`,`b`.`dxtype` AS `diag_type`,`a`.`doctor` AS `dr`,'' AS `episode`,'IT' AS `codeset`,`a`.`date_update` AS `d_update` from (`opd`.`opd` `a` left join `opd`.`odiag` `b` on(((`b`.`regdate` = `a`.`regdate`) and (`b`.`hn` = `a`.`hn`) and (`b`.`frequency` = `a`.`frequency`)))) where (left(`b`.`diag`,1) in ('S','T','V','W','X','Y')) order by `a`.`regdate` desc limit 1000
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `drug`;
CREATE ALGORITHM=UNDEFINED SQL SECURITY DEFINER VIEW `drug` AS select `opd`.`drug_order_opd`.`hn` AS `hn`,`opd`.`drug_order_opd`.`frequency` AS `seq`,`opd`.`drug_order_opd`.`regdate` AS `date_serve`,`opd`.`drug_order_opd`.`time_order` AS `time_serve`,`opd`.`drug_order_opd`.`namedrug` AS `drug_name`,`opd`.`drug_order_opd`.`amount` AS `qty`,(select `l`.`UnitName` from `hos`.`itemlist` `l` where (`l`.`itemcode` = `opd`.`drug_order_opd`.`codedrug`)) AS `unit`,(select `l`.`Line1` from `hos`.`itemlabel` `l` where (`l`.`code` = `opd`.`drug_order_opd`.`item_usage`)) AS `usage_line1`,(select `l`.`Line2` from `hos`.`itemlabel` `l` where (`l`.`code` = `opd`.`drug_order_opd`.`item_usage`)) AS `usage_line2`,(select `l`.`Line3` from `hos`.`itemlabel` `l` where (`l`.`code` = `opd`.`drug_order_opd`.`item_usage`)) AS `usage_line3` from `opd`.`drug_order_opd` where (`opd`.`drug_order_opd`.`regdate` between (curdate() + interval -(1) year) and curdate())
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `hospital`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `hospital` AS select `hosdata`.`confighos`.`codehos` AS `provider_code`,`hosdata`.`confighos`.`nameHos` AS `provider_name` from `hosdata`.`confighos`
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `lab`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `lab` AS select `l`.`hn` AS `hn`,`l`.`frequency` AS `seq`,`l`.`regdate` AS `date_serve`,concat(`l`.`namelab`,'[',`s`.`labname`,']') AS `lab_name`,`s`.`result_lab` AS `lab_result`,`s`.`normal_lab` AS `standard_result`,`l`.`time_order` AS `time_serve`,'OPD' AS `IOPD` from (`opd`.`lab_order_opd` `l` left join `opd`.`result_lab_opd` `s` on(((`s`.`regdate` = `l`.`regdate`) and (`s`.`hn` = `l`.`hn`) and (`s`.`frequency` = `l`.`frequency`) and (`s`.`orderno` = `l`.`orderno`) and (`s`.`labcode` = `l`.`codelab`)))) where (`l`.`regdate` between (curdate() + interval -(1) year) and curdate()) union select `l`.`hn` AS `hn`,`l`.`frequency` AS `seq`,`l`.`regdate` AS `date_serve`,concat(`l`.`namelab`,'[',`s`.`labname`,']') AS `lab_name`,`s`.`result_lab` AS `lab_result`,`s`.`normal_lab` AS `standard_result`,`l`.`time_order` AS `time_serve`,'PCU' AS `IOPD` from (`pcu`.`lab_order_pcu` `l` left join `pcu`.`result_lab_pcu` `s` on(((`s`.`regdate` = `l`.`regdate`) and (`s`.`hn` = `l`.`hn`) and (`s`.`frequency` = `l`.`frequency`) and (`s`.`orderno` = `l`.`orderno`) and (`s`.`labcode` = `l`.`codelab`)))) where (`l`.`regdate` between (curdate() + interval -(1) year) and curdate())
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `person`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `person` AS select `a`.`hn` AS `PatientID`,`a`.`hn` AS `hn`,(case when (convert(`a`.`pttitle` using utf8) = convert('นาย' using utf8)) then 'นาย' when (convert(`a`.`pttitle` using utf8) = convert('นาง' using utf8)) then 'นาง' when ((convert(`a`.`pttitle` using utf8) = convert('นางสาว' using utf8)) or (convert(`a`.`pttitle` using utf8) = convert('น.ส.' using utf8))) then 'นางสาว' when (convert(`a`.`pttitle` using utf8) = convert('ด.ช.' using utf8)) then 'ด.ช' when (convert(`a`.`pttitle` using utf8) = convert('ด.ญ.' using utf8)) then 'ด.ญ.' else 'ด.ญ.' end) AS `title_code`,convert(`a`.`ptfname` using utf8) AS `fname`,convert(`a`.`ptlname` using utf8) AS `lname`,replace(replace(`a`.`cardid`,'-',''),'_','') AS `CID`,(case when (`a`.`ptsex` = 'SX1') then '1' when (`a`.`ptsex` = 'SX2') then '2' else '9' end) AS `sex_code`,date_format(`a`.`ptdob`,'%Y-%m-%d') AS `birthdate`,(case when (`a`.`married` = 'MA1') then '1' when (`a`.`married` in ('MA2','MA3','MA4','MA5')) then '2' when (`a`.`married` = 'MA6') then '3' else '9' end) AS `marry_status`,(case when (`a`.`ptnation` = '99') then '99' when (`a`.`ptnation` = '44') then '44' when (`a`.`ptnation` = '56') then '56' else '999' end) AS `nationality`,(case when (`a`.`ptrace` = '99') then '1' when (`a`.`ptrace` = '44') then '2' when (`a`.`ptrace` = '56') then '3' else '999' end) AS `citizenship`,(case when (`a`.`religion` = 'RL1') then '1' when (`a`.`religion` = 'RL2') then '2' when (`a`.`religion` = 'RL3') then '3' else '8' end) AS `religion`,`a`.`ptaddress` AS `addr`,`a`.`ptvillage` AS `vill`,concat(`a`.`ptprovince`,`a`.`ptamphur`,`a`.`pttambon`) AS `addCode`,`a`.`ptphone` AS `Tel`,concat(convert(date_format(`a`.`updatedate`,'%Y%m%d') using tis620),(case when isnull(`a`.`timereg`) then '000000' else replace(`a`.`timereg`,':','') end)) AS `last_update`,'N' AS `occupation` from `pt`.`pt` `a` where (left(`a`.`hn`,1) <> 'x') order by `a`.`hn` desc
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `procedure`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `procedure` AS select `opd`.`ooper`.`hn` AS `hn`,`opd`.`ooper`.`frequency` AS `seq`,`opd`.`ooper`.`regdate` AS `date_serve`,`opd`.`ooper`.`oper` AS `procedure_code`,`opd`.`ooper`.`descrip` AS `procedure_name`,'00:00' AS `time_serve`,`opd`.`ooper`.`regdate` AS `start_date`,'00:00' AS `start_time`,`opd`.`ooper`.`regdate` AS `end_date`,'00:00' AS `end_time` from `opd`.`ooper`
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `profile`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY INVOKER VIEW `profile` AS select `pt`.`pt`.`hn` AS `hn`,replace(`pt`.`pt`.`cardid`,'-','') AS `cid`,`pt`.`pt`.`pttitle` AS `title_name`,`pt`.`pt`.`ptfname` AS `first_name`,`pt`.`pt`.`ptlname` AS `last_name` from `pt`.`pt`
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `refer`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `refer` AS select `hosdata`.`sendrefer`.`hn` AS `hn`,`hosdata`.`sendrefer`.`regdate` AS `date_serve`,`hosdata`.`sendrefer`.`frequency` AS `seq`,`hosdata`.`sendrefer`.`sendtohos` AS `hcode_to`,(select `h`.`name` from `hos`.`hospitals` `h` where (`h`.`OFF_ID` = `hosdata`.`sendrefer`.`sendtohos`)) AS `name_to`,`hosdata`.`sendrefer`.`diagnosis` AS `reason`,`hosdata`.`sendrefer`.`timerefer` AS `time_serve` from `hosdata`.`sendrefer`
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `sendward`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `sendward` AS select '10928' AS `hospcode`,`bb`.`roomname` AS `wardcode`,sum(if((`a`.`datedsc` = '0000-00-00'),'1','0')) AS `new_case`,(`bb`.`bed` - sum(if((`a`.`datedsc` = '0000-00-00'),'1','0'))) AS `empty_bad`,(`bb`.`bed` - sum(if((`a`.`datedsc` = '0000-00-00'),'1','0'))) AS `discharge`,0 AS `death` from (`ipd`.`ipd` `a` left join `hos`.`roomno` `bb` on((`bb`.`roomcode` = `a`.`now_ward`))) where ((`a`.`now_ward` like '%WARD%') and (not((`bb`.`roomname` like '%home%'))) and (left(`a`.`an`,1) <> 'x')) group by `a`.`now_ward`
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `service`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `service` AS select `opd`.`opd`.`hn` AS `hn`,`opd`.`opd`.`frequency` AS `seq`,`opd`.`opd`.`regdate` AS `date`,`opd`.`opd`.`hpressure` AS `bp`,`opd`.`opd`.`lpressure` AS `bp1`,`opd`.`opd`.`pulse` AS `puls`,time_format(`opd`.`opd`.`timestart`,'%H:%i:%s') AS `time_serve` from `opd`.`opd` where ((left(`opd`.`opd`.`hn`,1) <> 'x') and (`opd`.`opd`.`regdate` between (curdate() + interval -(3) year) and curdate()) and ((`opd`.`opd`.`timestart` <> '') or isnull(`opd`.`opd`.`timestart`) or (`opd`.`opd`.`timestart` <> '__:__')))
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `vaccine`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `vaccine` AS select `opd`.`ptvaccine`.`hn` AS `hn`,`opd`.`ptvaccine`.`regdate` AS `date_serve`,if(isnull(`opd`.`ptvaccine`.`time_vacc`),'00:00',`opd`.`ptvaccine`.`time_vacc`) AS `time_serve`,`opd`.`ptvaccine`.`code` AS `vaccine_code`,`opd`.`ptvaccine`.`name` AS `vaccine_name` from `opd`.`ptvaccine` union select `pcu`.`ptvaccine`.`hn` AS `hn`,`pcu`.`ptvaccine`.`regdate` AS `date_serve`,if(isnull(`pcu`.`ptvaccine`.`time_vacc`),'00:00',`pcu`.`ptvaccine`.`time_vacc`) AS `time_serve`,`pcu`.`ptvaccine`.`code` AS `vaccine_code`,`pcu`.`ptvaccine`.`name` AS `vaccine_name` from `pcu`.`ptvaccine`
;

-- Removing temporary table and create final VIEW structure
DROP TABLE IF EXISTS `ward`;
CREATE ALGORITHM=TEMPTABLE SQL SECURITY DEFINER VIEW `ward` AS select `cc`.`roomcode` AS `ward`,`cc`.`roomname` AS `name`,`cc`.`spclty` AS `spclty`,concat(`cc`.`std_code`) AS `sss_code`,count(0) AS `bedcount`,(case when (`cc`.`spclty` = 'N') then 1 else 0 end) AS `bedspecial` from ((`hos`.`hosbed` `a` left join `ipd`.`ipd` `b` on(((`b`.`bed` = `a`.`code`) and (`b`.`bed_type` = `a`.`bedtype`)))) left join `hos`.`roomno` `cc` on((`cc`.`roomcode` = `b`.`now_ward`))) where (`b`.`datedsc` = '0000-00-00') group by `cc`.`roomcode`
;

/*!40103 SET TIME_ZONE=IFNULL(@OLD_TIME_ZONE, 'system') */;
/*!40101 SET SQL_MODE=IFNULL(@OLD_SQL_MODE, '') */;
/*!40014 SET FOREIGN_KEY_CHECKS=IFNULL(@OLD_FOREIGN_KEY_CHECKS, 1) */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40111 SET SQL_NOTES=IFNULL(@OLD_SQL_NOTES, 1) */;


