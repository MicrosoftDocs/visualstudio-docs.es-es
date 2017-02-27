---
title: "How to: Create Types by using Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Clr.ClrAttributesDialog"
helpviewer_keywords: 
  - "custom attributes, applying"
  - "class diagrams, creating types"
  - "classes [Visual Studio], creating with Class Designer"
  - "Class Designer [Visual Studio], creating classes"
  - "types [Visual Studio], class diagrams"
  - "attributes [Visual Studio], applying custom"
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# How to: Create Types by using Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para diseñar nuevos tipos para proyectos de Visual C\# .NET y Visual Basic .NET, créelos en un diagrama de clases.  Para visualizar los tipos existentes, vea [How to: View Existing Types \(Class Designer\)](../ide/how-to-view-existing-types-class-designer.md).  
  
-   [Crear un tipo nuevo](#CreateType)  
  
-   [Aplicar un atributo personalizado a un tipo](#CustAttributeType)  
  
-   [Aplicar un atributo personalizado a un miembro de tipo](#CustAttributeMember)  
  
##  <a name="CreateType"></a> Crear un tipo nuevo  
  
1.  En el cuadro de herramientas, en Diseñador de clases, arrastre uno de estos a un diagrama de clase:  
  
    -   **Clase** o **Clase abstracta**  
  
    -   **Enum**  
  
    -   **Interfaz**  
  
    -   **Estructura** \(VB\) o **Struct** \(C\#\)  
  
    -   **Delegate**  
  
    -   **Módulo** \(solo en VB\)  
  
2.  Escriba un nombre para el tipo.  Después seleccione su nivel de acceso.  
  
3.  Seleccione el archivo donde desea agregar el código inicial para el tipo:  
  
    -   Para crear un archivo nuevo y agregarlo al proyecto actual, seleccione **Crear nuevo archivo** y escriba un nombre de archivo.  
  
    -   Para agregar código a un archivo existente, seleccione **Agregar al archivo existente**.  
  
         Si la solución tiene un proyecto que comparte código en varias aplicaciones, puede agregar un nuevo tipo a un diagrama de clases del proyecto de la aplicación, pero solo si el archivo de clases correspondiente está en el mismo proyecto de la aplicación o en el proyecto compartido.  
  
4.  Ahora agregue otros elementos para definir el tipo:  
  
    |||  
    |-|-|  
    |**For**|**Add**|  
    |Clases, clases abstractas, estructuras o structs|Métodos, propiedades, campos, eventos, constructores \(método\), destructores \(método\) y constantes que definen el tipo|  
    |Enumeraciones|Valores de campo que constituyen la enumeración|  
    |Interfaces|Métodos, propiedades y eventos que constituyen la interfaz|  
    |Delegate|Parámetros que definen el delegado|  
    |Module|Métodos, propiedades, campos, eventos, constructores \(método\) y constantes que definen el módulo|  
  
     Vea [Crear miembros](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a> Aplicar un atributo personalizado a un tipo  
  
1.  Haga clic en la forma del tipo en un diagrama de clases.  
  
2.  En la ventana Propiedades, junto a la propiedad **Atributos personalizados** del tipo, haga clic en el botón de puntos suspensivos \(\_\).  
  
3.  Agregue uno o varios atributos personalizados, uno por línea.  No los encierre entre corchetes.  
  
     Cuando haya acabado, los atributos personalizados se aplicarán al tipo.  
  
##  <a name="CustAttributeMember"></a> Aplicar un atributo personalizado a un miembro de tipo  
  
1.  Haga clic en el nombre del miembro, en la forma del tipo en un diagrama de clases o en la fila en la ventana Detalles de clase.  
  
2.  En la ventana Propiedades, busque la propiedad **Atributos personalizados** del miembro.  
  
3.  Agregue uno o varios atributos personalizados, uno por línea.  No los encierre entre corchetes.  
  
     Cuando haya acabado, los atributos personalizados se aplicarán al tipo.  
  
## Vea también  
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Creating and Configuring Type Members \(Class Designer\)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)