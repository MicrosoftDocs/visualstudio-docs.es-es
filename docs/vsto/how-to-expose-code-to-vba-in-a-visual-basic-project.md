---
title: Procedimiento Exponer código a VBA en un proyecto de Visual Basic
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7a534d32dc8e9352c10a214fbd70ec361b82aed1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900997"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Procedimiento Exponer código a VBA en un proyecto de Visual Basic
  Puede exponer código en un [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] proyectos a Visual Basic para aplicaciones (VBA) si desea que los dos tipos de código para interactuar entre sí.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 El proceso de Visual Basic es diferente del proceso de Visual C#. Para obtener más información, vea [Cómo: Exponer código a VBA en un Visual C&#35; proyecto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 El proceso es diferente para el código en una clase de elemento host para el código en otras clases:  
  
- [Exponer código en una clase de elemento host](#HostItemCode)  
  
- [Exponer código que no está en una clase de elemento host](#NonHostItem)  
  
  ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: ¿Llamar a código VSTO desde VBA? ](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> Exponer código en una clase de elemento host  
 Para habilitar código VBA llamar a código de Visual Basic en una clase de elemento host, establezca el **EnableVbaCallers** propiedad del elemento host en **True**.  
  
 Para ver un tutorial que muestra cómo exponer un método de una clase de elemento host y, a continuación, llamarlo desde VBA, vea [Tutorial: Llamar a código desde VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Para obtener más información sobre los elementos host, consulte [elementos Host y hospedar información general sobre controles](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Para exponer el código de un elemento host en VBA  
  
1.  Abra o cree un nivel de documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] proyecto que se basa en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros y que ya contenga código VBA.  
  
     Para obtener más información acerca de los formatos de archivo de documento que admiten macros, vea [combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esta característica no se puede utilizar en proyectos de plantilla de Word.  
  
2.  Asegúrese de que se puede ejecutar sin preguntar al usuario que habilite macros código VBA del documento. Puede confiar en la ejecución de código VBA si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en la configuración del Centro de confianza de Word o Excel.  
  
3.  Agregue la propiedad, método o evento que desea exponer a una de las clases de elemento host en el proyecto de VBA y declare el nuevo miembro como **pública**. El nombre de la clase depende de la aplicación:  
  
    -   En una palabra proyecto, la clase de elemento host denominada `ThisDocument` de forma predeterminada.  
  
    -   En un proyecto de Excel, las clases de elemento de host se denominan `ThisWorkbook`, `Sheet1`, `Sheet2`, y `Sheet3` de forma predeterminada.  
  
4.  Establecer el **EnableVbaCallers** propiedad del elemento host para **True**. Esta propiedad está disponible en el **propiedades** ventana cuando se abre en el diseñador del elemento host.  
  
     Después de establecer esta propiedad, Visual Studio establece automáticamente el **ReferenceAssemblyFromVbaProject** propiedad **True**.  
  
    > [!NOTE]  
    >  Si el documento o libro aún no contiene código VBA o si no es de confianza para ejecutar código VBA del documento, recibirá un mensaje de error al establecer el **EnableVbaCallers** propiedad **True**. Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento en esta situación.  
  
5.  Haga clic en **Aceptar** en el mensaje que se muestra. Este mensaje para recordarle que si agrega código VBA al libro o documento mientras se está ejecutando el proyecto desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], el código de VBA se perderá la próxima vez que compile el proyecto. Esto es porque el documento en la carpeta de salida de compilación se sobrescribe cada vez que compila el proyecto.  
  
     En este punto, Visual Studio configura el proyecto para que el proyecto de VBA puede llamar al ensamblado. Visual Studio también agrega una propiedad denominada `CallVSTOAssembly` a la `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, o `Sheet3` módulo en el proyecto VBA. Puede utilizar esta propiedad para tener acceso a los miembros públicos de la clase que expuso a VBA.  
  
6.  Compile el proyecto.  
  
##  <a name="NonHostItem"></a> Exponer código que no está en una clase de elemento host  
 Para habilitar código VBA llamar a código de Visual Basic que no está en una clase de elemento host, modifique el código, por lo que es visible a VBA.  
  
### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Para exponer código que no está en una clase de elemento host a VBA  
  
1.  Abra o cree un nivel de documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] proyecto que se basa en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros y que ya contenga código VBA.  
  
     Para obtener más información acerca de los formatos de archivo de documento que admiten macros, vea [combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Esta característica no se puede utilizar en proyectos de plantilla de Word.  
  
2.  Asegúrese de que se puede ejecutar sin preguntar al usuario que habilite macros código VBA del documento. Puede confiar en la ejecución de código VBA si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en la configuración del Centro de confianza de Word o Excel.  
  
3.  Agregue el miembro que desea exponer a VBA a una clase pública en el proyecto y declare el nuevo miembro como **pública**.  
  
4.  Aplique el siguiente <xref:System.Runtime.InteropServices.ComVisibleAttribute> y <xref:Microsoft.VisualBasic.ComClassAttribute> atributos a la clase que está exponiendo a VBA. Estos atributos hacen que la clase sea visible para VBA.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Reemplazar el método **GetAutomationObject** de una clase de elemento host del proyecto para devolver una instancia de la clase que está exponiendo a VBA. En el siguiente ejemplo se da por supuesto que expone una clase denominada `DocumentUtilities` a VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Abra el documento (para Word) o el Diseñador de la hoja de cálculo (para Excel) en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  En la ventana **Propiedades** , seleccione la propiedad **ReferenceAssemblyFromVbaProject** y cambie el valor a **True**.  
  
    > [!NOTE]  
    >  Si el documento o libro aún no contiene código VBA o si no es de confianza para ejecutar código VBA del documento, recibirá un mensaje de error al establecer el **ReferenceAssemblyFromVbaProject** propiedad **True** . Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento en esta situación.  
  
8.  Haga clic en **Aceptar** en el mensaje que se muestra. Este mensaje para recordarle que si agrega código VBA al libro o documento mientras se está ejecutando el proyecto desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], el código de VBA se perderá la próxima vez que compile el proyecto. Esto es porque el documento en la carpeta de salida de compilación se sobrescribe cada vez que compila el proyecto.  
  
     En este punto, Visual Studio configura el proyecto para que el proyecto de VBA puede llamar al ensamblado. Visual Studio también agrega un método denominado `GetManagedClass` al proyecto VBA. Puede llamar a este método desde cualquier lugar en el proyecto VBA para tener acceso a la clase que expuso a VBA.  
  
9. Compile el proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Tutorial: Llamar a código desde VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Cómo: Exponer código a VBA en un Visual C&#35; proyecto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
