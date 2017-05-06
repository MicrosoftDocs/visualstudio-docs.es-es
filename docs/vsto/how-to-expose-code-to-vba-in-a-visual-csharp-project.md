---
title: "C&#243;mo: Exponer c&#243;digo a VBA en un proyecto de Visual C#"
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
  - "VBA [desarrollo de Office en Visual Studio], exponer código en personalizaciones en el nivel del documento"
  - "Visual C# [desarrollo de Office en Visual Studio], exponer código en VBA"
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# C&#243;mo: Exponer c&#243;digo a VBA en un proyecto de Visual C# #
  Puede exponer código de un proyecto de Visual C\# a código de Visual Basic para Aplicaciones \(VBA\) si desea que los dos tipos de código interactúen entre sí.  
  
 El proceso de Visual C\# es diferente del proceso de Visual Basic.  Para obtener más información, vea [Cómo: Exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Exponer código en un proyecto de Visual C\#  
 Para permitir que el código de VBA llame a código de un proyecto de Visual C\#, modifique el código de forma que esté visible para COM y, a continuación, establezca la propiedad **ReferenceAssemblyFromVbaProject** en **True** en el diseñador.  
  
 Para tener acceso a un tutorial que muestra cómo llamar a un método de un proyecto de Visual C\# desde VBA, vea [Tutorial: llamar a código desde VBA en un proyecto de Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### Para exponer código de un proyecto de Visual C\# a VBA  
  
1.  Abra o cree un proyecto en el nivel del documento basado en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros y que ya contenga código de VBA.  
  
     Para obtener más información sobre los formatos de archivo de documento que admiten macros, vea [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esta característica no se puede usar en los proyectos de plantilla de Word.  
  
2.  Asegúrese de que el código de VBA del documento se puede ejecutar sin pedir al usuario que habilite las macros.  Puede confiar en que el código de VBA se ejecute si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en las opciones del Centro de confianza de Word o Excel.  
  
3.  Agregue el miembro que desea exponer a VBA a una clase pública del proyecto y declare el nuevo miembro como **public**.  
  
4.  Aplique los siguientes atributos <xref:System.Runtime.InteropServices.ComVisibleAttribute> y <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> a la clase que expone a VBA.  Estos atributos hacen que la clase sea visible para COM, pero sin generar una interfaz de clase.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Invalide el método **GetAutomationObject** de una clase de elemento host del proyecto para devolver una instancia de la clase que expone a VBA:  
  
    -   Si expone una clase de elemento host a VBA, invalide el método **GetAutomationObject** que pertenece a esta clase y devuelva la instancia actual de la clase.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Si expone una clase que no es un elemento host a VBA, invalide el método **GetAutomationObject** de cualquier elemento host del proyecto y devuelva una instancia de la clase de elemento no host.  Por ejemplo, en el código siguiente se supone que expone una clase denominada `DocumentUtilities` a VBA.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Para obtener más información acerca de los elementos de host, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Extraiga una interfaz de la clase que expone a VBA.  En el cuadro de diálogo **Extraer interfaz**, seleccione los miembros públicos que desea incluir en la declaración de interfaz.  Para obtener más información, vea [Extraer interfaz &#40;Refactorización, C&#35;&#41;](../csharp-ide/extract-interface-refactoring-csharp.md).  
  
7.  Agregue la palabra clave **public** a la declaración de interfaz.  
  
8.  Haga la interfaz visible para COM agregando el siguiente atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> a la interfaz.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Abra el documento \(para Word\) o la hoja de cálculo \(para Excel\) en el diseñador en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. En la ventana **Propiedades**, seleccione la propiedad **ReferenceAssemblyFromVbaProject** y cambie el valor a **True**.  
  
    > [!NOTE]  
    >  Si el libro o el documento aún no contiene código de VBA o si el código de VBA del documento no dispone de confianza para ejecutarse, recibirá un mensaje de error al establecer la propiedad **ReferenceAssemblyFromVbaProject** en **True**.  Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento cuando se da esta situación.  
  
11. Haga clic en **Aceptar** en el mensaje que aparece.  Este mensaje le recuerda que si agrega código de VBA al libro o el documento al ejecutar el proyecto desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], el código de VBA se perderá la próxima vez que compile el proyecto.  Esto se debe a que el documento de la carpeta de salida de la compilación se sobrescribe cada vez se genera el proyecto.  
  
     Llegado a este punto, Visual Studio configura el proyecto de forma que el proyecto de VBA pueda llamar al ensamblado.  Visual Studio también agrega un método denominado `GetManagedClass` al proyecto de VBA.  Puede llamar a este método desde cualquier parte del proyecto de VBA para tener acceso a la clase que expuso a VBA.  
  
12. Compile el proyecto.  
  
## Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Tutorial: llamar a código desde VBA en un proyecto de Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Cómo: Exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  