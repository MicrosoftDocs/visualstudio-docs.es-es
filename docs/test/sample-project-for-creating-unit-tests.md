---
title: "Proyecto de ejemplo para crear pruebas unitarias | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "prueba unitaria (ejemplo) [Visual Studio]"
  - "pruebas unitarias, ejemplos"
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "mlearned"
manager: "douge"
---
# Proyecto de ejemplo para crear pruebas unitarias
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este código de ejemplo se proporciona para su uso en los siguientes tutoriales:  
  
-   [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  Este tutorial le guía por los pasos necesarios para crear y personalizar pruebas unitarias, ejecutarlas y examinar los resultados.  
  
-   [Tutorial: Ejecutar pruebas y ver la cobertura del código](http://msdn.microsoft.com/es-es/d4aab8e2-2140-4975-b4e3-41ef3fa944c8).  Este tutorial muestra cómo ver los datos de cobertura de código, que indican la proporción de código del proyecto que se está probando.  
  
-   [Tutorial: Utilizar la utilidad de prueba de la línea de comandos](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md).  En este tutorial, utilice la utilidad de línea de comandos MSTest.exe para ejecutar pruebas y ver los resultados.  
  
## Código de ejemplo  
 El único error intencionado en este ejemplo es que, en el método Debit, "m\_balance \+\= amount" debe tener un signo menos, no más, antes del signo igual.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 \/\* Las compañías, organizaciones, productos, nombres de dominio, direcciones de correo electrónico, logotipos, personas, lugares y eventos que se citan a modo de ejemplo son ficticios.  No se pretende indicar, ni debe deducirse, ninguna asociación con compañías, organizaciones, productos, dominios, direcciones de correo electrónico, logotipos, personas, lugares o hechos reales.  \*\/  
  
## Trabajar con el código  
 Para trabajar con este código, primero tiene que crear un proyecto para él en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Siga los pasos de la sección "Preparar el tutorial" en [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## Vea también  
 [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Tutorial: Ejecutar pruebas y ver la cobertura del código](http://msdn.microsoft.com/es-es/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Tutorial: Utilizar la utilidad de prueba de la línea de comandos](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md)