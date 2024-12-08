---
title: ERD
sidebar_position: 1
---

# Модель данных

import Drawio from '@theme/Drawio'
import diagram from '!!raw-loader!./model.drawio';

<Drawio content={diagram} editable={false} />


## TeanPro

| Сущность        | Атрибут       | Тип данных        | Описание                                                                 | Связи                          |
|----------------|----------------|------------------|------------------------------------------------------------------------|---------------------------------|
| Skills          | SkillID        | INT              | Уникальный идентификатор навыка                                          | Связь многие ко многим с Employees через таблицу EmployeeSkills |
|                | SkillName      | VARCHAR(255)     | Название навыка                                                         |                                 |
| Employees       | EmployeeID     | INT              | Уникальный идентификатор сотрудника                                     | Связь один ко многим с JobTitles, EmployeeSkills, EmployeeProject |
|                | EmployeeName   | VARCHAR(255)     | Имя сотрудника                                                         |                                 |
|                | Gender         | ENUM('Male', 'Female') | Пол сотрудника                                                          |                                 |
|                | HireDate       | DATE             | Дата найма сотрудника                                                 |                                 |
|                | Workload       | DECIMAL(5, 2)    | Рабочая нагрузка (процент), значение от 0 до 100                       |                                 |
| JobTitles       | JobTitleID     | INT              | Уникальный идентификатор должности                                    | Связь многие к одному с Employees |
|                | EmployeeID     | INT              | Ссылка на сотрудника, который занимает данную должность               |                                 |
|                | JobTitle       | VARCHAR(50)      | Название должности                                                    |                                 |
|                | ExperienceLevel | VARCHAR(50)    | Градация специалистов для определения уровня опыта                     |                                 |
| EmployeeSkills  | EmployeeID     | INT              | Ссылка на сотрудника                                                   | Связь многие ко многим с Employees и Skills |
|                | SkillID        | INT              | Ссылка на навык                                                         |                                 |
| Project         | ProjectID      | INT              | Уникальный идентификатор проекта                                      | Связь многие ко многим с Employees через таблицу EmployeeProject |
|                | PrName         | VARCHAR(255)     | Название проекта                                                      |                                 |
|                | Description    | TEXT             | Описание проекта                                                      |                                 |
|                | StartDate      | DATE             | Дата начала проекта                                                   |                                 |
|                | Budget         | DECIMAL(15, 2)   | Бюджет проекта                                                        |                                 |
| EmployeeProject  | EmployeeID     | INT              | Ссылка на сотрудника, который работает над проектом                   | Связь многие ко многим с Employees и Project |
|                | ProjectID      | INT              | Ссылка на проект, в котором участвует сотрудник                       |                                 |