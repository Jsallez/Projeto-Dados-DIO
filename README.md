# Projeto - Processando e transformando dados com Power BI  - Bootcamp de Ciência de Dados DIO

Este projeto foi desenvolvido como parte do Bootcamp de Ciência de Dados da Digital Innovation One (DIO), com o objetivo de concluir os requisitos estabelecidos pelo curso.

O projeto conciste em criar um banco de dados no Azure, adicionar os dados utilizando comando no BASH e MySQL, tratar os dados no Power Query do Power Bi e criar um breve relatório demonstrativo. 

# Descrição da transformação de dados

- Coluna “Salário” da tabela employee modificada de número decimal para número decimal fixo.
- O campos address da tabela employee foi separado em “Number_address”, “Street”, “City” e “State”
- Foram mescladas as colunas employee e departament, com o objetivo de definir uma nova tabela.(azure_company supervisor_departament) que contem somente os colaboradores que gerenciam um departamento.
- Removidas colunas sem utilidade de todas as tabelas
- Adicionado uma tabela (azure_company count_dependent) com a o quantitativo de colaboradores que contém dependentes e a soma de dependentes.
    
    → Codigo da consulta: 
    
    ```sql
    SELECT e.Ssn, COUNT(d.Essn) AS DependentCount
    FROM employee e
    LEFT JOIN dependent d ON e.Ssn = d.Essn
    GROUP BY e.Ssn;
    ```
    

- Adicionado uma tabela (azure_company collaborator_supervisor) destacando quem são os colaboradores e quais os seus respectivos supervisores.
    
    → Código de consulta:
    

```sql
SELECT
c.Fname AS Collaborator_FirstName,
c.Minit AS Collaborator_MiddleInitial,
c.Lname AS Collaborator_LastName,
c.Ssn AS Collaborator_SSN,
c.Bdate AS Collaborator_BirthDate,
c.Address AS Collaborator_Address,
c.Sex AS Collaborator_Gender,
c.Salary AS Collaborator_Salary,
c.Dno AS Collaborator_DepartmentNumber,
s.Fname AS Supervisor_FirstName,
s.Minit AS Supervisor_MiddleInitial,
s.Lname AS Supervisor_LastName,
s.Ssn AS Supervisor_SSN
FROM
employee c
LEFT JOIN
employee s ON c.Super_ssn = s.Ssn;
```

- Colunas de nome e sobrenome dos colaboradores mescladas em todas as tabelas.
- Mesclada as tabelas (azure_company departament e azure_company dept_locations) em uma nova tabela. (azure_company departament_and_location) contendo os departamentos e as localizações. A opção mesclar foi utilizada com o objetivo de manter as associações entre os departamentos e a localização informada.
- Mesclada a tabela (azure_company departament_and_location com a tabela (azure_compay supervisor_departamente) nomeada de (azure_company departament_location).



## Ferramentas utilizadas:
- Banco de dados Azure, MySQL e Power Bi.
