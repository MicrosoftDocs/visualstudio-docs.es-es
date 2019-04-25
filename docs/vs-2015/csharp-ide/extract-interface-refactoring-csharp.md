---
title: Extraer interfaz (refactorización, C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55b24facd3a9ec935277a42c211a64d824ed6d7f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116750"
---
# <a name="extract-interface-refactoring-c"></a>Extraer interfaz (Refactorización, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extraer interfaz es una operación de refactorización que proporciona una manera sencilla para crear una nueva interfaz con miembros que se originan en una clase existente, estructura o interfaz.  
  
 Cuando varios clientes utilizan el mismo subconjunto de miembros de una clase, estructura o interfaz, o cuando varias clases, estructuras o interfaces tienen un subconjunto de miembros en común, puede ser útil integrar el subconjunto de miembros en una interfaz. Para obtener más información sobre el uso de interfaces, vea [Interfaces](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).  
  
 Extraer interfaz genera una interfaz en un archivo nuevo y coloca el cursor al principio del archivo nuevo. Puede especificar qué miembros se extraerán a la nueva interfaz, el nombre de la nueva interfaz y el nombre del archivo generado mediante el **Extraer interfaz** cuadro de diálogo.  
  
### <a name="to-use-extract-interface"></a>Para utilizar Extraer interfaz  
  
1. Cree una aplicación de consola denominada `ExtractInterface`y, a continuación, reemplace `Program` con el código siguiente  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2. Con el cursor situado en `MethodB`y haga clic en **Extraer interfaz** en el **refactorizar** menú.  
  
     El **Extraer interfaz** aparece el cuadro de diálogo.  
  
     También puede escribir el método abreviado de teclado CTRL + R, que se va a mostrar el **Extraer interfaz** cuadro de diálogo.  
  
     También puede haga clic en el mouse, apuntar a **refactorizar**y, a continuación, haga clic en **Extraer interfaz** para mostrar el **Extraer interfaz** cuadro de diálogo.  
  
3. Haga clic en **seleccionar todo**.  
  
4. Haga clic en **Aceptar**.  
  
     Consulte el nuevo archivo, IProtoA.cs y el código siguiente:  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>Comentarios  
 Esta característica solo está accesible cuando el cursor se coloca en la clase, struct o interfaz que contiene a los miembros que le gustaría extraer. Cuando el cursor está en esta posición, invoque la operación de refactorización Extraer interfaz.  
  
 Cuando se invoca Extraer interfaz en una clase o struct, la lista de bases e interfaces se modifica para incluir el nuevo nombre de interfaz. Cuando se invoca Extraer interfaz en una interfaz, no se modifica la lista de bases e interfaces.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)