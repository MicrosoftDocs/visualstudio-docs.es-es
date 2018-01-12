---
title: "Cómo: exponer código a VBA en un proyecto de Visual C# | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a4794f1cde57f365ec4ec98251763e8d0e839ae0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Cómo: Exponer código a VBA en un proyecto de Visual C#
  Puede exponer el código de un proyecto de Visual C# en Visual Basic para aplicaciones (VBA) si desea que los dos tipos de código que interactúan entre sí.  
  
 El proceso de Visual C# es diferente del proceso de Visual Basic. Para obtener más información, consulte [Cómo: exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>Exponer código en un proyecto de Visual C#  
 Para habilitar el código VBA llamar a código en un proyecto de Visual C#, modifique el código por lo que es visible para COM y, a continuación, establezca el **ReferenceAssemblyFromVbaProject** propiedad **True** en el diseñador.  
  
 Para ver un tutorial que muestra cómo llamar a un método en un proyecto de Visual C# desde VBA, vea [Tutorial: llamar a código desde VBA en un Visual C &#35; Proyecto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Exponer código en un proyecto de Visual C# a VBA  
  
1.  Abra o cree un proyecto de nivel de documento que se basa en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros y que ya contenga código VBA.  
  
     Para obtener más información acerca de los formatos de archivo de documento que admiten macros, vea [combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esta característica no se puede utilizar en proyectos de plantilla de Word.  
  
2.  Asegúrese de que el código de VBA en el documento se puede ejecutar sin preguntar al usuario que habilite macros. Puede confiar en la ejecución de código VBA si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en la configuración del Centro de confianza de Word o Excel.  
  
3.  Agregar el miembro que desea exponer a VBA a una clase pública en el proyecto y declare el nuevo miembro como **público**.  
  
4.  Aplique el siguiente <xref:System.Runtime.InteropServices.ComVisibleAttribute> y <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributos a la clase que está exponiendo a VBA. Estos atributos hacen que la clase sea visible para COM, pero sin generar una interfaz de clase.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Invalidar el **GetAutomationObject** método de una clase de elemento host del proyecto para devolver una instancia de la clase que está exponiendo a VBA:  
  
    -   Si expone una clase de elemento host a VBA, invalide el **GetAutomationObject** método que pertenece a esta clase y devolver la instancia actual de la clase.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Si expone una clase que no es un elemento host a VBA, invalide el **GetAutomationObject** método de cualquier host de elemento en el proyecto y devolver una instancia de la clase de elemento no es de host. Por ejemplo, el código siguiente supone que expone una clase denominada `DocumentUtilities` a VBA.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Para obtener más información sobre los elementos host, consulte [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Extraer una interfaz de la clase que está exponiendo a VBA. En el **Extraer interfaz** cuadro de diálogo, seleccione los miembros públicos que se van a incluir en la declaración de interfaz. Para obtener más información, vea [Extraer interfaz refactorización &#40; C &#35; &#41; ](/visualstudio/csharp-ide/extract-interface-refactoring-csharp).  
  
7.  Agregar el **público** palabra clave a la declaración de interfaz.  
  
8.  Hacer que la interfaz visible para COM agregando las siguientes <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribuir a la interfaz.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Abra el documento (para Word) o la hoja de cálculo (para Excel) en el diseñador en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. En la ventana **Propiedades** , seleccione la propiedad **ReferenceAssemblyFromVbaProject** y cambie el valor a **True**.  
  
    > [!NOTE]  
    >  Si el documento o libro aún no contiene código VBA o si no es de confianza para ejecutar código VBA en el documento, recibirá un mensaje de error al establecer el **ReferenceAssemblyFromVbaProject** propiedad **True**. Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento en esta situación.  
  
11. Haga clic en **Aceptar** en el mensaje que se muestra. Este mensaje le recuerda que si agrega VBA al libro de código o cuando se ejecuta el proyecto a partir de documentos [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], el código VBA se perderá la próxima vez que compile el proyecto. Esto es porque el documento en la compilación del resultado de la carpeta se sobrescribe cada vez que compile el proyecto.  
  
     En este punto, Visual Studio configura el proyecto para que el proyecto de VBA puede llamar al ensamblado. Visual Studio también agrega un método denominado `GetManagedClass` al proyecto de VBA. Puede llamar a este método desde cualquier lugar en el proyecto VBA para tener acceso a la clase que expuso a VBA.  
  
12. Compile el proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Tutorial: Llamar a código desde VBA en una Visual C &#35; Proyecto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Cómo: Exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  