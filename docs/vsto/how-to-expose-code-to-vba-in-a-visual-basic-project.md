---
title: "C&#243;mo: Exponer c&#243;digo a VBA en un proyecto de Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], exponer código"
  - "exponer código en VBA"
  - "elementos host [desarrollo de Office en Visual Studio], exponer código en VBA"
  - "VBA [desarrollo de Office en Visual Studio], exponer código en personalizaciones en el nivel del documento"
  - "Visual Basic [desarrollo de Office en Visual Studio], exponer código en VBA"
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# C&#243;mo: Exponer c&#243;digo a VBA en un proyecto de Visual Basic
  Puede exponer código en un proyecto de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] a código de Visual Basic para Aplicaciones \(VBA\) si desea que los dos tipos de código interactúen entre sí.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 El proceso de Visual Basic es diferente del proceso de Visual C\#.  Para obtener más información, vea [Cómo: Exponer código a VBA en un proyecto de Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 El proceso es diferente para el código de una clase de elemento host que para el código de otras clases:  
  
-   [Exponer código en una clase de elemento host](#HostItemCode)  
  
-   [Exponer código que no se encuentra en una clase de elemento host](#NonHostItem)  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Dispone de una demostración en vídeo relacionada en [How Do I: Call VSTO Code from VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> Exponer código en una clase de elemento host  
 Para permitir que el código de VBA llame al código de Visual Basic en una clase de elemento host, establezca la propiedad **EnableVbaCallers** del elemento host en **True**.  
  
 Para obtener un tutorial en el que se muestra cómo exponer un método de una clase de elemento host y, a continuación, invocarlo desde VBA, vea [Tutorial: Llamar a código de VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  Para obtener más información acerca de los elementos de host, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
#### Para exponer código de un elemento host a VBA  
  
1.  Abra o cree un proyecto de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] de nivel de documento basado en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros y que ya contenga código de VBA.  
  
     Para obtener más información sobre los formatos de archivo de documento que admiten macros, vea [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esta característica no se puede usar en los proyectos de plantilla de Word.  
  
2.  Asegúrese de que el código de VBA del documento se puede ejecutar sin pedir al usuario que habilite las macros.  Puede confiar en que el código de VBA se ejecute si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en las opciones del Centro de confianza de Word o Excel.  
  
3.  Agregue la propiedad, el método o el evento que desea exponer a VBA a una de las clases de elemento host de su proyecto y declare el nuevo miembro como **Public**.  El nombre de la clase depende de la aplicación:  
  
    -   En un proyecto de Word, la clase de elemento host se denomina de forma predeterminada `ThisDocument`.  
  
    -   En un proyecto de Excel, las clases de elemento host se denominan de forma predeterminada `ThisWorkbook`, `Sheet1`, `Sheet2`y `Sheet3`.  
  
4.  Establezca la propiedad **EnableVbaCallers** del elemento host en **True**.  Esta propiedad está disponible en la ventana **Propiedades** cuando el elemento host se abre en el diseñador.  
  
     Después de establecer esta propiedad, Visual Studio establece automáticamente la propiedad **ReferenceAssemblyFromVbaProject** en **True**.  
  
    > [!NOTE]  
    >  Si el libro o el documento aún no contiene código de VBA o si el código de VBA del documento no dispone de confianza para ejecutarse, recibirá un mensaje de error al establecer la propiedad **EnableVbaCallers** en **True**.  Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento cuando se da esta situación.  
  
5.  Haga clic en **Aceptar** en el mensaje que aparece.  Este mensaje le recuerda que si agrega código de VBA al libro o el documento mientras ejecuta el proyecto desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], el código de VBA se perderá la próxima vez que compile el proyecto.  Esto se debe a que el documento de la carpeta de salida de la compilación se sobrescribe cada vez se genera el proyecto.  
  
     Llegado a este punto, Visual Studio configura el proyecto de forma que el proyecto de VBA pueda llamar al ensamblado.  Visual Studio también agrega una propiedad denominada `CallVSTOAssembly` al módulo `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2` o `Sheet3` en el proyecto de VBA.  Puede utilizar esta propiedad para tener acceso a los miembros públicos de la clase que expuso a VBA.  
  
6.  Compile el proyecto.  
  
##  <a name="NonHostItem"></a> Exponer código que no se encuentra en una clase de elemento host  
 Para permitir que el código de VBA llame al código de Visual Basic que no está en una clase de elemento host, modifique el código de forma que resulte visible para VBA.  
  
#### Para exponer código que no está en una clase de elemento host a VBA  
  
1.  Abra o cree un proyecto de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] de nivel de documento basado en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros y que ya contenga código de VBA.  
  
     Para obtener más información sobre los formatos de archivo de documento que admiten macros, vea [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esta característica no se puede usar en los proyectos de plantilla de Word.  
  
2.  Asegúrese de que el código de VBA del documento se puede ejecutar sin pedir al usuario que habilite las macros.  Puede confiar en que el código de VBA se ejecute si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en las opciones del Centro de confianza de Word o Excel.  
  
3.  Agregue el miembro que desea exponer a VBA a una clase pública del proyecto y declare el nuevo miembro como **public**.  
  
4.  Aplique los siguientes atributos <xref:System.Runtime.InteropServices.ComVisibleAttribute> y <xref:Microsoft.VisualBasic.ComClassAttribute> a la clase que expone a VBA.  Estos atributos hacen que la clase sea visible para VBA.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Invalide el método **GetAutomationObject** de una clase de elemento host del proyecto para devolver una instancia de la clase que expone a VBA.  El ejemplo de código siguiente supone que expone una clase denominada `DocumentUtilities` a VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Abra el diseñador de documentos \(para Word\) o de hojas de cálculo \(para Excel\) en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  En la ventana **Propiedades**, seleccione la propiedad **ReferenceAssemblyFromVbaProject** y cambie el valor a **True**.  
  
    > [!NOTE]  
    >  Si el libro o el documento aún no contiene código de VBA o si el código de VBA del documento no dispone de confianza para ejecutarse, recibirá un mensaje de error al establecer la propiedad **ReferenceAssemblyFromVbaProject** en **True**.  Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento cuando se da esta situación.  
  
8.  Haga clic en **Aceptar** en el mensaje que aparece.  Este mensaje le recuerda que si agrega código de VBA al libro o el documento mientras ejecuta el proyecto desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], el código de VBA se perderá la próxima vez que compile el proyecto.  Esto se debe a que el documento de la carpeta de salida de la compilación se sobrescribe cada vez se genera el proyecto.  
  
     Llegado a este punto, Visual Studio configura el proyecto de forma que el proyecto de VBA pueda llamar al ensamblado.  Visual Studio también agrega un método denominado `GetManagedClass` al proyecto de VBA.  Puede llamar a este método desde cualquier parte del proyecto de VBA para tener acceso a la clase que expuso a VBA.  
  
9. Compile el proyecto.  
  
## Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Tutorial: Llamar a código de VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Cómo: Exponer código a VBA en un proyecto de Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  