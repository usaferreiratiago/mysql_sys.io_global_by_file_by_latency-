# mysql_sys.io_global_by_file_by_latency-

SELECT 
    `sys`.`format_path`(`performance_schema`.`file_summary_by_instance`.`FILE_NAME`) AS `file`,
    `performance_schema`.`file_summary_by_instance`.`COUNT_STAR` AS `total`,
    FORMAT_PICO_TIME(`performance_schema`.`file_summary_by_instance`.`SUM_TIMER_WAIT`) AS `total_latency`,
    `performance_schema`.`file_summary_by_instance`.`COUNT_READ` AS `count_read`,
    FORMAT_PICO_TIME(`performance_schema`.`file_summary_by_instance`.`SUM_TIMER_READ`) AS `read_latency`,
    `performance_schema`.`file_summary_by_instance`.`COUNT_WRITE` AS `count_write`,
    FORMAT_PICO_TIME(`performance_schema`.`file_summary_by_instance`.`SUM_TIMER_WRITE`) AS `write_latency`,
    `performance_schema`.`file_summary_by_instance`.`COUNT_MISC` AS `count_misc`,
    FORMAT_PICO_TIME(`performance_schema`.`file_summary_by_instance`.`SUM_TIMER_MISC`) AS `misc_latency`
FROM
    `performance_schema`.`file_summary_by_instance`
ORDER BY `performance_schema`.`file_summary_by_instance`.`SUM_TIMER_WAIT` DESC
