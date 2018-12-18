---
title: Código de ejemplo para crear pruebas unitarias
description: En este artículo se proporciona código de ejemplo que se puede probar con pruebas unitarias en Visual Studio.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: deddf46a479e0ab8d4e0bebbaf3fffe4d90b622d
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51293452"
---
# <a name="sample-code-for-testing"></a>Código de ejemplo para pruebas

Este código de ejemplo contiene una clase, *BankAccount*, con diversos métodos que se pueden probar en las pruebas unitarias.

El código se usa en los siguientes tutoriales:

- [Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Este tutorial le guía por los pasos necesarios para crear y personalizar pruebas unitarias, ejecutarlas y examinar los resultados.
- [Usar la utilidad de prueba de la línea de comandos](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). En este tutorial, use la utilidad de línea de comandos *MSTest.exe* para ejecutar pruebas y ver los resultados.

## <a name="sample-code"></a>Código de ejemplo

El único error intencionado en este ejemplo es que, en el método Debit, "m_balance += amount" debe tener un signo menos, no más, antes del signo igual.

```csharp
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

/* Las compañías, organizaciones, productos, nombres de dominio, direcciones de correo electrónico, logotipos, personas, lugares y eventos que se citan a modo de ejemplo son ficticios. No se pretende indicar, ni debe deducirse, ninguna asociación con compañías, organizaciones, productos, dominios, direcciones de correo electrónico, logotipos, personas, lugares o hechos reales. \*/

## <a name="create-the-project"></a>Crear el proyecto

Para trabajar con este código, primero cree un proyecto para él en Visual Studio. Siga los pasos para crear el proyecto en [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test).

## <a name="see-also"></a>Vea también

- [Tutorial: Crear y ejecutar pruebas unitarias en código administrado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Tutorial: Usar la utilidad de prueba de la línea de comandos](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
