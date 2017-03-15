---
title: "Reordenar par&#225;metros de refactorizaci&#243;n (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.reorder"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactorización [C#], Reordenar parámetros"
  - "Reordenar parámetros (refactorización) [C#]"
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Reordenar par&#225;metros de refactorizaci&#243;n (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Reorder Parameters` es una operación de refactorización de Visual C\# que proporciona una manera sencilla de cambiar el orden de los parámetros para los métodos, indizadores y delegados.  `Reorder Parameters` cambia la declaración y, en todas las ubicaciones donde se llama al miembro, los parámetros se reorganizan para reflejar el nuevo orden.  
  
 Para realizar la operación `Reorder Parameters`, sitúe el cursor sobre o a un lado de un método, indizador o delegado.  Una vez colocado el cursor, invoque la operación `Reorder Parameters` usando el método abreviado de teclado o haciendo clic en el comando del menú contextual.  
  
> [!NOTE]
>  No puede reordenar el primer parámetro de un método de extensión.  
  
### Para reordenar parámetros  
  
1.  Cree una biblioteca de clases denominada `ReorderParameters` y, a continuación, reemplace `Class1` por el ejemplo de código siguiente.  
  
    ```c#  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Coloque el cursor en `MethodB`, en la declaración de método o la llamada al método.  
  
3.  En el menú **Refactorizar**, haga clic en **Reordenar parámetros**.  
  
     Aparece el cuadro de diálogo **Reordenar parámetros**.  
  
4.  En el cuadro de diálogo **Reordenar parámetros**, seleccione `int i` en la lista **Parámetros** y, a continuación, haga clic en el botón de la flecha hacia abajo.  
  
     Como alternativa, puede arrastrar `int i` después de `bool b` en la lista **Parámetros**.  
  
5.  En el cuadro de diálogo **Reordenar parámetros**, haga clic en **Aceptar**.  
  
     Si selecciona la opción **Vista previa de los cambios de referencia** en el cuadro de diálogo **Reordenar parámetros**, aparecerá el cuadro de diálogo **Obtener vista previa de cambios \- Reordenar parámetros**.  Proporciona una vista previa de los cambios realizados en la lista de parámetros de `MethodB` en la firma y la llamada al método.  
  
    1.  Si aparece el cuadro de diálogo **Obtener vista previa de cambios \- Reordenar parámetros**, haga clic en **Aplicar**.  
  
         En este ejemplo, se actualiza la declaración de método y todos los sitios de llamada al método `MethodB`.  
  
## Comentarios  
 Puede reordenar los parámetros de una declaración de método o una llamada al método.  Sitúe el cursor sobre la declaración de método o delegado o al lado de éstos, pero no en el cuerpo.  
  
## Vea también  
 [Refactorización \(C\#\)](../csharp-ide/refactoring-csharp.md)