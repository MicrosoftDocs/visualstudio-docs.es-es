---
title: Procedimiento Exponer código a VBA en un C# proyecto
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f0b3f004f6aebed6426238a081369c7d50e15f5
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648514"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Procedimiento Exponer código a VBA en un proyecto de Visual C#
  Puede exponer el código de un proyecto de Visual C# en Visual Basic para aplicaciones (VBA) si desea que los dos tipos de código para interactuar entre sí.  
  
 El proceso de Visual C# es diferente del proceso de Visual Basic. Para obtener más información, vea [Cómo: Exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="expose-code-in-a-visual-c-project"></a>Exponer código en un proyecto de Visual C#  
 Para habilitar código VBA llamar a código en un proyecto de Visual C#, modifique el código por lo que es visible para COM y, a continuación, establezca el **ReferenceAssemblyFromVbaProject** propiedad **True** en el diseñador.  
  
 Para ver un tutorial que muestra cómo llamar a un método en un proyecto de Visual C# desde VBA, vea [Tutorial: Llamar a código desde VBA en un Visual C&#35; proyecto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Exponer código en un proyecto de Visual C# a VBA  
  
1. Abra o cree un proyecto de nivel de documento que se basa en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros y que ya contenga código VBA.  
  
    Para obtener más información acerca de los formatos de archivo de documento que admiten macros, vea [combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
   > [!NOTE]  
   >  Esta característica no se puede utilizar en proyectos de plantilla de Word.  
  
2. Asegúrese de que se puede ejecutar sin preguntar al usuario que habilite macros código VBA del documento. Puede confiar en la ejecución de código VBA si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en la configuración del Centro de confianza de Word o Excel.  
  
3. Agregue el miembro que desea exponer a VBA a una clase pública en el proyecto y declare el nuevo miembro como **pública**.  
  
4. Aplique el siguiente <xref:System.Runtime.InteropServices.ComVisibleAttribute> y <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributos a la clase que está exponiendo a VBA. Estos atributos hacen que la clase sea visible para COM, pero sin generar una interfaz de clase.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   [System.Runtime.InteropServices.ClassInterface(  
       System.Runtime.InteropServices.ClassInterfaceType.None)]  
   ```  
  
5. Invalidar el **GetAutomationObject** método de una clase de elemento host en el proyecto para devolver una instancia de la clase que está exponiendo a VBA:  
  
   - Si expone una clase de elemento host a VBA, invalide el **GetAutomationObject** método que pertenece a esta clase y devuelve la instancia actual de la clase.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return this;  
     }  
     ```  
  
   - Si expone una clase que no es un elemento host a VBA, invalide el **GetAutomationObject** método de cualquier host en el proyecto de elemento y devolver una instancia de la clase de elemento que no sean de host. Por ejemplo, el código siguiente supone que expone una clase denominada `DocumentUtilities` a VBA.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return new DocumentUtilities();  
     }  
     ```  
  
     Para obtener más información sobre los elementos host, consulte [elementos Host y hospedar información general sobre controles](../vsto/host-items-and-host-controls-overview.md).  
  
6. Extraer una interfaz de la clase que está exponiendo a VBA. En el **Extraer interfaz** cuadro de diálogo, seleccione los miembros públicos que se van a incluir en la declaración de interfaz. Para obtener más información, consulte [refactorización de extracción interfaz](../ide/reference/extract-interface.md).
  
7. Agregar el **pública** palabra clave para la declaración de interfaz.  
  
8. Hacer que la interfaz visible para COM agregando el siguiente <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo a la interfaz.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   ```  
  
9. Abra el documento (para Word) o una hoja de cálculo (para Excel) en el diseñador en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. En la ventana **Propiedades** , seleccione la propiedad **ReferenceAssemblyFromVbaProject** y cambie el valor a **True**.  
  
    > [!NOTE]  
    >  Si el documento o libro aún no contiene código VBA o si no es de confianza para ejecutar código VBA del documento, recibirá un mensaje de error al establecer el **ReferenceAssemblyFromVbaProject** propiedad **True**. Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento en esta situación.  
  
11. Haga clic en **Aceptar** en el mensaje que se muestra. Este mensaje le recuerda que si agrega VBA de código en el libro o documento al ejecutar el proyecto de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], el código de VBA se perderá la próxima vez que se compila el proyecto. Esto es porque el documento en la compilación de salida de carpeta se sobrescribe cada vez que se compila el proyecto.  
  
     En este punto, Visual Studio configura el proyecto para que el proyecto de VBA puede llamar al ensamblado. Visual Studio también agrega un método denominado `GetManagedClass` al proyecto VBA. Puede llamar a este método desde cualquier lugar en el proyecto VBA para tener acceso a la clase que expuso a VBA.  
  
12. Compile el proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Tutorial: Llamar a código desde VBA en un Visual C&#35; proyecto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Cómo: Exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  