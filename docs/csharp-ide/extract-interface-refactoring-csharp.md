---
title: "Extraer interfaz (Refactorizaci&#243;n, C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractinterface"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Extraer interfaz (operación de refactorización) [C#]"
  - "refactorización [C#], Extraer interfaz"
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extraer interfaz (Refactorizaci&#243;n, C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Extraer interfaz es una operación de refactorización que ofrece una manera sencilla de crear una nueva interfaz con miembros originados a partir de una clase, struct o interfaz existente.  
  
 Cuando varios clientes utilizan el mismo subconjunto de miembros de una clase, struct o interfaz, o cuando varias clases, structs o interfaces tienen un subconjunto de miembros en común, puede resultar de gran utilidad integrar el subconjunto de miembros en una interfaz.  Para obtener más información sobre el uso de interfaces, vea [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Extraer interfaz genera una interfaz en un nuevo archivo y coloca el cursor al principio del nuevo archivo.  Puede especificar qué miembros se extraerán a la nueva interfaz, el nombre de ésta y el nombre del archivo generado mediante el cuadro de diálogo **Extraer interfaz**.  
  
### Para utilizar Extraer interfaz  
  
1.  Cree una aplicación de consola denominada `ExtractInterface` y, a continuación, reemplace `Program` por el ejemplo siguiente.  
  
    ```c#  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Con el cursor colocado en `MethodB`, haga clic en **Extraer interfaz** en el menú **Refactorizar**.  
  
     Aparecerá el cuadro de diálogo **Extraer interfaz**.  
  
     También puede presionar el método abreviado de teclado CTRL\+R, I para mostrar el cuadro de diálogo **Extraer interfaz**.  
  
     O bien, puede hacer clic con el botón secundario del mouse, seleccionar **Refactorizar** y, a continuación, hacer clic en **Extraer interfaz** para mostrar el cuadro de diálogo **Extraer interfaz**.  
  
3.  Haga clic en **Seleccionar todo**.  
  
4.  Haga clic en **Aceptar**.  
  
     Aparece el nuevo archivo, IProtoA.cs y el código siguiente:  
  
    ```c#  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## Comentarios  
 Únicamente se puede tener acceso a esta característica cuando el cursor está situado en la clase, el struct o la interfaz que contiene los miembros que se desea extraer.  Cuando el cursor está en esta posición, invoque la operación de refactorización Extraer interfaz.  
  
 Cuando se invoca Extraer interfaz en una clase o struct, la lista de bases e interfaces se modifica, a fin de incluir el nombre de la nueva interfaz.  Cuando se invoca Extraer interfaz en una interfaz, la lista de bases e interfaces no se modifica.  
  
## Vea también  
 [Refactorización \(C\#\)](../csharp-ide/refactoring-csharp.md)