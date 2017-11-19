---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: "Extraer interfaz (refactorización, C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4ed81f6f0fbcc2e72fd57d7706b051dcdf7bea75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="extract-interface-refactoring-c"></a>Extraer interfaz (Refactorización, C#)
Extraer interfaz es una operación de refactorización que proporciona una manera sencilla para crear una nueva interfaz con miembros que se originan en una interfaz, struct o clase existente.  
  
 Cuando varios clientes utilizan el mismo subconjunto de miembros de una clase, estructura o interfaz, o cuando varias clases, structs o interfaces tienen un subconjunto de miembros en común, puede ser útil integrar el subconjunto de miembros en una interfaz. Para obtener más información sobre el uso de interfaces, vea [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Extraer interfaz genera una interfaz en un nuevo archivo y coloca el cursor al principio del nuevo archivo. Puede especificar qué miembros se extraerán a la nueva interfaz, el nombre de la nueva interfaz y el nombre del archivo generado mediante la **Extraer interfaz** cuadro de diálogo.  
  
### <a name="to-use-extract-interface"></a>Para utilizar Extraer interfaz  
  
1.  Cree una aplicación de consola denominada `ExtractInterface`y, a continuación, reemplace `Program` con el código siguiente  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Con el cursor situado en `MethodB`y haga clic en **Extraer interfaz** en el **refactorizar** menú.  
  
     El **Extraer interfaz** aparece el cuadro de diálogo.  
  
     También puede escribir el método abreviado de teclado CTRL + R, puede mostrar el **Extraer interfaz** cuadro de diálogo.  
  
     También puede hacer clic del mouse, apuntar a **refactorizar**y, a continuación, haga clic en **Extraer interfaz** para mostrar la **Extraer interfaz** cuadro de diálogo.  
  
3.  Haga clic en **seleccionar todo**.  
  
4.  Haga clic en **Aceptar**.  
  
     Verá el nuevo archivo, IProtoA.cs y el código siguiente:  
  
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
 Esta característica solo está disponible cuando el cursor se coloca en la clase, estructura o interfaz que contiene a los miembros que desea extraer. Cuando el cursor está en esta posición, invoque la operación de refactorización Extraer interfaz.  
  
 Cuando se invoca Extraer interfaz en una clase o un struct, la lista de bases e interfaces se modifica para incluir el nuevo nombre de interfaz. Cuando se invoca Extraer interfaz en una interfaz, no se modifica la lista de bases e interfaces.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](refactoring-csharp.md)