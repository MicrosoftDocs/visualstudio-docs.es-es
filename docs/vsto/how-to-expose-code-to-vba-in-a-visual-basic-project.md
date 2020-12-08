---
title: 'Cómo: exponer código a VBA en un proyecto de Visual Basic'
description: Obtenga información sobre cómo puede exponer código en un proyecto de Visual Basic al código de Visual Basic para Aplicaciones (VBA) Si desea que los dos tipos de código interactúen entre sí.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61f94ebb5ed0c5e76693ddc8c0717b6adf9222f3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845991"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Cómo: exponer código a VBA en un proyecto de Visual Basic
  Puede exponer el código de un [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] proyecto a Visual Basic para aplicaciones código (VBA) Si desea que los dos tipos de código interactúen entre sí.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 El proceso de Visual Basic es diferente del proceso de Visual C#. Para obtener más información, vea [Cómo: exponer código a VBA en un proyecto de&#35; de Visual C](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 El proceso es diferente para el código de una clase de elemento host que para el código de otras clases:

- [Exponer código en una clase de elemento host](#HostItemCode)

- [Exponer código que no está en una clase de elemento host](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Exponer código en una clase de elemento host
 Para permitir que el código VBA llame a Visual Basic código de una clase de elemento host, establezca la propiedad **EnableVbaCallers** del elemento host en **true**.

 Para ver un tutorial que muestra cómo exponer un método de una clase de elemento host y, a continuación, llamarlo desde VBA, vea [Tutorial: llamar a código desde VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Para obtener más información sobre los elementos host, vea [información general sobre elementos y controles](../vsto/host-items-and-host-controls-overview.md)host.

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Para exponer el código de un elemento host a VBA

1. Abra o cree un proyecto de nivel de documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] basado en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros, y que ya contenga código VBA.

     Para obtener más información sobre los formatos de archivo de documento que admiten macros, vea [combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Esta característica no se puede utilizar en proyectos de plantilla de Word.

2. Asegúrese de que el código VBA del documento puede ejecutarse sin preguntar al usuario si desea habilitar macros. Puede confiar en la ejecución de código VBA si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en la configuración del Centro de confianza de Word o Excel.

3. Agregue la propiedad, el método o el evento que desea exponer a VBA a una de las clases de elemento host del proyecto y declare el nuevo miembro como **público**. El nombre de la clase depende de la aplicación:

    - En un proyecto de Word, la clase de elemento host se denomina de `ThisDocument` forma predeterminada.

    - En un proyecto de Excel, las clases de elementos host se denominan `ThisWorkbook` , `Sheet1` , `Sheet2` y `Sheet3` de forma predeterminada.

4. Establezca la propiedad **EnableVbaCallers** para el elemento host en **true**. Esta propiedad está disponible en la ventana **propiedades** cuando el elemento host está abierto en el diseñador.

     Después de establecer esta propiedad, Visual Studio establece automáticamente la propiedad **ReferenceAssemblyFromVbaProject** en **true**.

    > [!NOTE]
    > Si el libro o documento no contiene código VBA o si el código VBA del documento no es de confianza para ejecutarse, recibirá un mensaje de error al establecer la propiedad **EnableVbaCallers** en **true**. Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento en esta situación.

5. Haga clic en **Aceptar** en el mensaje que se muestra. Este mensaje le recuerda que si agrega código VBA al libro o documento mientras ejecuta el proyecto desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , el código VBA se perderá la próxima vez que compile el proyecto. Esto se debe a que el documento de la carpeta de salida de la compilación se sobrescribe cada vez que se compila el proyecto.

     En este momento, Visual Studio configura el proyecto para que el proyecto de VBA pueda llamar al ensamblado. Visual Studio también agrega una propiedad denominada `CallVSTOAssembly` al `ThisDocument` módulo, `ThisWorkbook` , `Sheet1` , `Sheet2` o del `Sheet3` proyecto de VBA. Puede usar esta propiedad para tener acceso a los miembros públicos de la clase que expuso a VBA.

6. Compile el proyecto.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Exponer código que no está en una clase de elemento host
 Para permitir que el código VBA llame a Visual Basic código que no está en una clase de elemento host, modifique el código para que sea visible para VBA.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Para exponer código que no está en una clase de elemento host a VBA

1. Abra o cree un proyecto de nivel de documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] basado en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros, y que ya contenga código VBA.

     Para obtener más información sobre los formatos de archivo de documento que admiten macros, vea [combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Esta característica no se puede utilizar en proyectos de plantilla de Word.

2. Asegúrese de que el código VBA del documento puede ejecutarse sin preguntar al usuario si desea habilitar macros. Puede confiar en la ejecución de código VBA si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en la configuración del Centro de confianza de Word o Excel.

3. Agregue el miembro que desea exponer a VBA a una clase pública del proyecto y declare el nuevo miembro como **público**.

4. Aplique los <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributos y siguientes <xref:Microsoft.VisualBasic.ComClassAttribute> a la clase que está exponiendo a VBA. Estos atributos hacen que la clase sea visible para VBA.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Reemplazar el método **GetAutomationObject** de una clase de elemento host del proyecto para devolver una instancia de la clase que está exponiendo a VBA. En el ejemplo de código siguiente se da por supuesto que expone una clase denominada `DocumentUtilities` a VBA.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. Abra el documento (para Word) o el diseñador de hojas de cálculo (para Excel) en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. En la ventana **Propiedades** , seleccione la propiedad **ReferenceAssemblyFromVbaProject** y cambie el valor a **True**.

    > [!NOTE]
    > Si el libro o documento no contiene código VBA o si el código VBA del documento no es de confianza para ejecutarse, recibirá un mensaje de error al establecer la propiedad **ReferenceAssemblyFromVbaProject** en **true**. Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento en esta situación.

8. Haga clic en **Aceptar** en el mensaje que se muestra. Este mensaje le recuerda que si agrega código VBA al libro o documento mientras ejecuta el proyecto desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , el código VBA se perderá la próxima vez que compile el proyecto. Esto se debe a que el documento de la carpeta de salida de la compilación se sobrescribe cada vez que se compila el proyecto.

     En este momento, Visual Studio configura el proyecto para que el proyecto de VBA pueda llamar al ensamblado. Visual Studio también agrega un método denominado `GetManagedClass` al proyecto de VBA. Puede llamar a este método desde cualquier lugar del proyecto de VBA para tener acceso a la clase que expuso a VBA.

9. Compile el proyecto.

## <a name="see-also"></a>Vea también
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Tutorial: llamar a código desde VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Cómo: exponer código a VBA en un proyecto de&#35; de Visual C](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
