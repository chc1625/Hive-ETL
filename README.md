# Hive-ETL
## 一个简单的Hive ETL操作

ETL:
- Extraction
- Transformation
- Load

场景： 
- 在MySQL中有emp表，不直接使用MySQL进行统计； 
- 而是先将MySQL中的emp表数据通过Sqoop框架，抽取到Hive中； 
- 然后使用Hive进行统计分析； 
- 最终将结果通过Sqoop框架导出到MySQL表中

流程分析： 
1. 在Hive中先创建一个emp对应的表：emp_m_to_h    
   代表是从MySQL中导入到Hive表中的数据  
2. 使用Sqoop将MySQL中的emp表导入到Hive的表：emp_m_to_h 
3. 创建Hive表：result_h_to_m    
   代表从Hive中导出到MySQL的结果数据 
4. 在hive中进行统计分析(每个部门多少人)，然后结果写入到Hive结果表：result_h_to_m 
5. 在MySQL中，创建表：result_a    
   代表最终的计算结果 
6. 将Hive结果表通过Sqoop导出到MySQL表：result_a
