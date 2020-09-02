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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667560"
---
# <a name="extract-interface-refactoring-c"></a>Extraer interfaz (Refactorización, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extract interface es una operación de refactorización que proporciona una manera fácil de crear una nueva interfaz con miembros que se originan a partir de una clase, estructura o interfaz existente.

 Cuando varios clientes usan el mismo subconjunto de miembros de una clase, estructura o interfaz, o cuando varias clases, estructuras o interfaces tienen un subconjunto de miembros en común, puede resultar útil incluir el subconjunto de miembros en una interfaz. Para obtener más información sobre el uso de interfaces, vea [interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).

 Extract interface genera una interfaz en un archivo nuevo y coloca el cursor al principio del nuevo archivo. Puede especificar qué miembros se van a extraer en la nueva interfaz, el nombre de la nueva interfaz y el nombre del archivo generado mediante el cuadro de diálogo **Extraer interfaz** .

### <a name="to-use-extract-interface"></a>Para usar Extract interface

1. Cree una aplicación de consola denominada `ExtractInterface` y, a continuación, reemplace `Program` por el código siguiente.

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. Con el cursor colocado en `MethodB` , haga clic en **Extraer interfaz** en el menú **refactorizar** .

     Aparece el cuadro de diálogo **Extraer interfaz** .

     También puede escribir el método abreviado de teclado CTRL + R, I para mostrar el cuadro de diálogo **Extraer interfaz** .

     También puede hacer clic con el botón secundario en el mouse, seleccionar **refactorizar**y, a continuación, hacer clic en **Extraer interfaz** para mostrar el cuadro de diálogo **Extraer interfaz** .

3. Haga clic en **seleccionar todo**.

4. Haga clic en **Aceptar**.

     Verá el nuevo archivo, IProtoA.cs, y el código siguiente:

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

## <a name="remarks"></a>Observaciones
 Esta característica solo es accesible cuando el cursor se coloca en la clase, estructura o interfaz que contiene los miembros que desea extraer. Cuando el cursor esté en esta posición, invoque la operación de refactorización extraer interfaz.

 Al invocar la interfaz de extracción en una clase o en una estructura, la lista de bases e interfaces se modifica para incluir el nuevo nombre de interfaz. Al invocar la interfaz de extracción en una interfaz, la lista de bases e interfaces no se modifica.

## <a name="see-also"></a>Consulte también
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)