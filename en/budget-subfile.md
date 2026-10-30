---
title: "Budget Subfile"
description: ""
published: false
date: '2021-06-29T15:27:54Z'
tags: ["MTS2", "Savegame/Subfiles"]
editor: markdown
dateCreated: '2019-08-10T01:21:29Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

<!-- unconverted template: about -->

This page pertains to the format of the **Budget** files within [Savegame](/savegame) files. These files may also be known as **Taxes**, which is how they are often labeled in [Reader](/reader).

## Specifications

NOTE: *\[Start Break\]* notes the start of a section where there are repeating sections. *\[End Break\]* notes the end of the section where there are repeating sections. Repeating sections can/may exist in multiple locations in the one file.

### Budget E990BE01

`Dword - File Size (number of bits that follow).`  
`10 Bytes - Unknown`  
`Qword - Total Funds`  
`Qword - Total Funds`  
`Qword - Total Loans Borrowed Amount`  
`QWord - Monthly Expense`  
`220 Bytes - Unknown. There's some sort of pattern here in these 220 bytes.`  
  
`Dword - R$ Current Tax Rate`  
`Dword - R$ Max Tax Rate (Seems the Max Tax Rate available in-game is Hard Coded)`  
`112 bytes - Unknown, Mostly Zero's`  
`Qword - R$ Tax Income Monthly Estimate`  
`Dword - R$$ Current Tax Rate`  
`Dword - R$$ Max Tax Rate`  
`112 bytes - Unknown`  
`Qword - R$$ Tax Income Monthly Estimate`  
`Dword - R$$$ Current Tax Rate`  
`Dword - R$$$ Max Tax Rate`  
`112 Bytes - Unknown`  
`Qword -R$$$ Tax Income Monthly Estimate`  
`Dword - CS-$ Current Tax Rate`  
`Dword - CS-$ Max Tax Rate`  
`112 Bytes - Unknown`  
`QWord - CS-$ Tax Income Monthly Estimate`  
`Dword - CS-$$ Current Tax Rate`  
`Dword - CS-$$ Max Tax Rate`  
`112 Bytes - Unknown`  
`Qword - CS-$$ Tax Income Monthly Estimate`  
`Dword - CS-$$$ Current Tax Rate`  
`Dword - CS-$$$ Max Tax Rate`  
`112 bytes - Unknown`  
`Qword - CS-$$$ Tax Income Monthly Estimate`  
`Dword - CO-$$ Current Tax Rate`  
`Dword - CO-$$ Max Tax Rate`  
`112 bytes - Unknown`  
`Qword - CO-$$ Tax Income Monthly Estiamate`  
`Dword - CO-$$$ Current Tax Rate`  
`Dword - CO-$$$ Max Current Tax Rate`  
`112 byte - Unknown`  
`Qword - CO-$$$ Tax Income Monthly Estimate`  
`Dword - IAG Current Tax Rate`  
`Dword - IAG Max Tax Rate`  
`112 bytes - Unknown`  
`Qword - IAG Tax Income Monthly Estimate`  
`Dword - ID Current Tax Rate`  
`Dword - ID Max Tax Rate`  
`112 Bytes - Unknown`  
`Qword - ID Tax Income Monthly Estimate`  
`Dword - IM Current Tax Rate`  
`Dword - IM Max Tax Rate`  
`112 Bytes - Unknown`  
`Qword - IM Tax Income Monthly Estimate`  
`Dword - IHT Tax Current Rate`  
`Dword - IHT Max Tax Rate`  
`112 Bytes - Unknown`  
`Qword - IHT Tax Income Monthly Estimate `  
  
`X Bytes - Unknown, also changes.`  
  
`Dword - Total Number of Loans Issued.`  
`        This is probably an identifier for this section, identifying the`  
`        length of this particular Section in  terms of the number of Loans on issue.`  
`[Start break]`  
`  8 Bytes - Unknown.`  
`  QWord - Loan Amount borrowed (Individual Loan).`  
`  Qword1 -Total Loan Repayments (total repayments over course of loan).`  
`  Qword - Unknown.`  
`  QWord - Unknown.`  
`  QWord - Monthly Loan Repayment Amount (Individual Loan)`  
`  Qword - Loan Amount Owed (Individual Loan)`  
`[End Break]`  
`(Repeat above section for each loan.)`  
  
`8 Bytes - Unknown`  
`QWord - Monthly Income (Total) `  
`Qword - Unknown (maybe also monthly income?)`  
`Qword - Monthly Expenses (Total) `  
`Qword - Unknown (maybe also monthly expense?)`  
  
`Dword - (Possibly) number of Sections that follow.`  
`[Start Break]`  
`  Dword - Unknown. Same value as following Dword.`  
`  Dword - Unknown. Same value as previous Dword`  
`  Dword - Length of section name.`  
`  String - Section Name, i.e. different areas of the Budget.`  
`  Qword - Monthly Expense Estimate of Section.`  
`  Qword - Monthly Income Estimate of Section.`  
`  Dword - Equals the number of Dwords that follow.`  
`  XxDwords - See Previous Dword just above to get the number of Dwords for here - Unknown.`  
`[End Break]`  
`(Repeat above section for each different Budget Deparment.)`

### Budget AA313C9F (cSC4LineItem)

`Dword - File Size of Section (number of bytes).`  
`DWord - CRC`  
`DWord - Memory`  
`Word  - Version (0x0004)`  
`Dword - Length of Section Name. If this is zero, seems as though`  
`        there is no section name, or valid section for that matter,`  
`        but rather the  section is just a "Fill" section??.`  
`String - Section name, i.e. different areas of the Budget & individual items.`  
`DWord - Number of "Section Item" Items (where applicable, as not all budget`  
`        items give details as to how many there are of a particular item).`  
`Dword - Unknown.`  
`QWord - Section Monthly Cost (Expense) - For items if they were at standard 100% efficiency.`  
`QWord - Section Monthly Estimate (Expense) - Current Month Actual Amount charged against the Budget.`  
`Qword - Section Monthly Estimate (Revenue) - Current Month Actual Amount credited to Budget.`  
`Variable X Bytes - Unknown, number of remaining bytes depends on each sections' Dword file size above. `  
`(Repeat as necessary as per above for each section.)`

### Budget E990BFFC (cSC4DepartmentBudget)

`Dword - File Size of Section (number of bytes).`  
`Dword - CRC`  
`Dword - Memory`  
`Word  - Major version (0x000a)`  
`5 Bytes - Unknown.`  
`Dword - Length of Section Name.`  
`String - Section Name, i.e. different areas/categories within the Budget.`  
`21 Bytes - Unknown`  
`Dword - Length of array to follow, listing different items within the Budget Department areas.`  
`    DWORD - Memory address of line item`  
`    DWORD - 0xaa313c9f (Type ID of cSC4LineItem)`  
`Dword - Length of array to follow, listing the buildings.`  
`    DWORD - Memory address of building`  
`    DWORD - 0xa9bd882d (Type ID of Building subfile)`  
`    DWORD - Purpose ID of the Budget Item (for example, School Coverage is 0x4a5654ba, School Staff is 0xea5654b6, ...)`  
`Dword - Unknown, might be a memory address`  
`Dword - Unknown, might be a pointer type (0x6a3ff01c)`  
`(Repeat as necessary as per above for each section (for each budget item)).`
