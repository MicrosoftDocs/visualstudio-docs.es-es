---
title: 'Cómo: exponer código a VBA en un proyecto de C#'
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21d7672d3c08012e75d73ee8bf4d9816b850eb2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544838"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Cómo: exponer código a VBA en un proyecto de Visual C#
  Puede exponer el código de un proyecto de Visual C# a código de Visual Basic para Aplicaciones (VBA) Si desea que los dos tipos de código interactúen entre sí.

 El proceso de Visual C# es diferente del proceso de Visual Basic. Para obtener más información, vea [Cómo: exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Exponer código en un proyecto de Visual C#
 Para que el código VBA pueda llamar a código en un proyecto de Visual C#, modifique el código para que sea visible para COM y, a continuación, establezca la propiedad **ReferenceAssemblyFromVbaProject** en **true** en el diseñador.

 Para ver un tutorial que muestra cómo llamar a un método en un proyecto de Visual C# desde VBA, vea [Tutorial: llamar a código desde VBA en un proyecto de&#35; de Visual C](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Para exponer el código de un proyecto de Visual C# a VBA

1. Abra o cree un proyecto de nivel de documento basado en un documento de Word, un libro de Excel o una plantilla de Excel que admita macros, y que ya contenga código VBA.

    Para obtener más información sobre los formatos de archivo de documento que admiten macros, vea [combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Esta característica no se puede utilizar en proyectos de plantilla de Word.

2. Asegúrese de que el código VBA del documento puede ejecutarse sin preguntar al usuario si desea habilitar macros. Puede confiar en la ejecución de código VBA si agrega la ubicación del proyecto de Office a la lista de ubicaciones de confianza en la configuración del Centro de confianza de Word o Excel.

3. Agregue el miembro que desea exponer a VBA a una clase pública del proyecto y declare el nuevo miembro como **público**.

4. Aplique los <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributos y siguientes <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> a la clase que está exponiendo a VBA. Estos atributos hacen que la clase sea visible para COM, pero sin generar una interfaz de clase.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Invalide el método **GetAutomationObject** de una clase de elemento host del proyecto para devolver una instancia de la clase que está exponiendo a VBA:

   - Si expone una clase de elemento host a VBA, invalide el método **GetAutomationObject** que pertenece a esta clase y devuelva la instancia actual de la clase.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Si expone una clase que no es un elemento host a VBA, invalide el método **GetAutomationObject** de cualquier elemento host del proyecto y devuelva una instancia de la clase de elemento que no es host. Por ejemplo, en el código siguiente se supone que expone una clase denominada `DocumentUtilities` a VBA.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Para obtener más información sobre los elementos host, vea [información general sobre elementos y controles](../vsto/host-items-and-host-controls-overview.md)host.

6. Extraiga una interfaz de la clase que está exponiendo a VBA. En el cuadro de diálogo **Extraer interfaz** , seleccione los miembros públicos que desee incluir en la declaración de la interfaz. Para obtener más información, consulte [Extraer interfaz refactorización](../ide/reference/extract-interface.md).

7. Agregue la palabra clave **Public** a la declaración de interfaz.

8. Haga que la interfaz sea visible para COM agregando el <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo siguiente a la interfaz.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Abra el documento (para Word) o la hoja de cálculo (para Excel) en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. En la ventana **Propiedades** , seleccione la propiedad **ReferenceAssemblyFromVbaProject** y cambie el valor a **True**.

    > [!NOTE]
    > Si el libro o el documento aún no contiene código VBA o si el código VBA del documento no es de confianza para ejecutarse, recibirá un mensaje de error al establecer la propiedad **ReferenceAssemblyFromVbaProject** en **true**. Esto se debe a que Visual Studio no puede modificar el proyecto de VBA del documento en esta situación.

11. Haga clic en **Aceptar** en el mensaje que se muestra. Este mensaje le recuerda que si agrega código VBA al libro o documento al ejecutar el proyecto desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , el código VBA se perderá la próxima vez que compile el proyecto. Esto se debe a que el documento de la carpeta de salida de la compilación se sobrescribe cada vez que se compila el proyecto.

     En este momento, Visual Studio configura el proyecto para que el proyecto de VBA pueda llamar al ensamblado. Visual Studio también agrega un método denominado `GetManagedClass` al proyecto de VBA. Puede llamar a este método desde cualquier lugar del proyecto de VBA para tener acceso a la clase que expuso a VBA.

12. Compile el proyecto.

## <a name="see-also"></a>Consulte también
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Tutorial: llamar a código desde VBA en un proyecto de&#35; de Visual C](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Cómo: exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
