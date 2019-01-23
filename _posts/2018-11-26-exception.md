---
layout: post
title:  "pl/sql中异常处理"
categories: Oracle pl/sql
tags: Oracle pl/sql
author: KeeperLee
---
* content
{:toc}
## 系统异常和自定义异常




>##### 系统异常之no_data_found(没有找到数据)





``` sql
--系统异常：no_data_found
set serveroutput on
declare 
    pename emp.ename%type;
begin
    --查询员工号为1234的员工姓名
    select ename into pename from emp where empno =1234;
exception
    when no_data_found then dbms_output.put_line('没有找到该员工');
    when others then dbms_output.put_line('其他异常');  
end;
/
```






>##### 系统异常之too_many_rows(select ... into 语句匹配多个行)





``` sql
--系统异常：tooo_many_rows
set serveroutput on
declare 
    pename emp.ename%type;
begin
    --查询所有10号部门的员工姓名
        select ename into pename from emp where deptno=10;
exception
    when too_many_rows then dbms_output.put_line('select into 匹配了多个行');
    when others then dbms_output.put_line('其他异常');
end;
/
```







>##### 系统异常之zero_divide(0不能做除数)





``` sql
--系统异常：zero_divide
set serveroutput on
declare 
    --定义一个基本变量
    pnum number;
begin
    pnum:=1/0;
exception
    when zero_divide then dbms_output.put_line('1：0不能被除');
                                          dbms_output.put_line('2：0不能被除');
    when others then dbms_output.put_line('其他异常');
end;
/
--then语句后面可以执行多条语句。
```



>##### 系统异常之value_error(转换异常)





``` sql
--系统异常：value_error
set serveroutput on
declare 
    --定义一个number类型的变量
    pnum number;
begin
    pnum:='abc';
exception
    when value_error then dbms_output.put_line('算术或者转换错误');
    when others then dbms_output.put_line('其他异常');
end;
/
```



>##### 自定义异常的抛出和捕获





``` sql
--自定义异常：查询50号部门的员工姓名（没有50号部门的员工）
set serveroutput on
declare
    --定义光标，代表50号部门的员工的姓名
    cursor cemp is select ename from emp where deptno=50;
    pename emp.ename%type;
    
    --自定义异常
    no_emp_found exception;
begin
    --打开光标
    open cemp;
    --直接取一个员工的姓名
    fetch cemp into pename;
    if cemp%notfound then
    --抛出异常
        raise no_emp_found;
    end if;
    --关闭光标
    --oracle自动启动pmon(process nomitor)资源处理进程，异常抛出后，oracle自动关闭光标
    close cemp;
    --捕获异常
exception
    when no_emp_found then dbms_output.put_line('没有找到员工');
    when others then dbms_output.put_line('其他异常');
end;
/
```