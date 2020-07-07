---
title: 'Tutorial: crear una extensión de proyecto de SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df10e2da9e6b4c31894dce0669e9aa0e580b92f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015077"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Tutorial: crear una extensión de proyecto de SharePoint
  En este tutorial se muestra cómo crear una extensión para los proyectos de SharePoint. Puede usar una extensión de proyecto para responder a eventos de nivel de proyecto, como cuando se agrega, se elimina o se cambia el nombre de un proyecto. También puede Agregar propiedades personalizadas o responder cuando cambia el valor de una propiedad. A diferencia de las extensiones de elemento de proyecto, las extensiones de proyecto no se pueden asociar a un tipo de proyecto de SharePoint concreto. Cuando se crea una extensión de proyecto, la extensión se carga cuando se abre cualquier tipo de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 En este tutorial, creará una propiedad booleana personalizada que se agrega a cualquier proyecto de SharePoint creado en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Cuando se establece en **true**, la nueva propiedad agrega, o asigna, una carpeta de recursos images al proyecto. Cuando se establece en **false**, se quita la carpeta images, si existe. Para obtener más información, consulte [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 En este tutorial se muestran las siguientes tareas:

- Crear una [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensión para los proyectos de SharePoint que hace lo siguiente:

  - Agrega una propiedad de proyecto personalizada al ventana Propiedades. La propiedad se aplica a cualquier proyecto de SharePoint.

  - Utiliza el modelo de objetos de proyecto de SharePoint para agregar una carpeta asignada a un proyecto.

  - Utiliza el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modelo de objetos de automatización (DTE) para eliminar una carpeta asignada del proyecto.

- Compilar un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para implementar el ensamblado de extensión de la propiedad de proyecto.

- Depurar y probar la propiedad del proyecto.

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] , SharePoint y [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- El parámetro de cadena de consulta [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. En este tutorial se usa la plantilla de **Proyecto VSIX** en el [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] para crear un paquete VSIX para implementar la extensión de propiedad de proyecto. Para obtener más información, vea [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear dos proyectos:

- Un proyecto VSIX para crear el paquete VSIX para implementar la extensión de proyecto.

- Proyecto de biblioteca de clases que implementa la extensión de proyecto.

  Comience el tutorial creando ambos proyectos.

#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **extensibilidad** .

    > [!NOTE]
    > Este nodo solo está disponible si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.

4. En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones del .NET Framework y, a continuación, elija la plantilla de **Proyecto VSIX** .

5. En el cuadro **nombre** , escriba **ProjectExtensionPackage**y elija el botón **Aceptar** .

     El proyecto **ProjectExtensionPackage** aparece en **Explorador de soluciones**.

#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución, elija **Agregar**y, a continuación, elija **nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#** o **Visual Basic** y, a continuación, elija **Windows**.

3. En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones del .NET Framework y, después, elija la plantilla de proyecto **biblioteca de clases** .

4. En el cuadro **nombre** , escriba **ProjectExtension**y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]agrega el proyecto **ProjectExtension** a la solución y abre el archivo de código predeterminado Class1.

5. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-project"></a>Configuración del proyecto
 Antes de escribir código para crear la extensión de proyecto, agregue los archivos de código y las referencias de ensamblado al proyecto de extensión.

#### <a name="to-configure-the-project"></a>Para configurar el proyecto

1. Agregue un archivo de código denominado **CustomProperty** al proyecto ProjectExtension.

2. Abra el menú contextual del proyecto **ProjectExtension** y, a continuación, elija **Agregar referencia**.

3. En el cuadro de diálogo **Administrador de referencias-CustomProperty** , elija el nodo **Framework** y, a continuación, active la casilla que hay junto a los ensamblados System. ComponentModel. Composition y System. Windows. Forms.

4. Elija el nodo **extensiones** , active la casilla situada junto a los ensamblados Microsoft. VisualStudio. SharePoint y EnvDTE y, a continuación, elija el botón **Aceptar** .

5. En **Explorador de soluciones**, en la carpeta **referencias** del proyecto **ProjectExtension** , elija **EnvDTE**.

6. En la ventana **propiedades** , cambie la propiedad **incrustar tipos de interoperabilidad** a **false**.

## <a name="define-the-new-sharepoint-project-property"></a>Definir la propiedad nuevo proyecto de SharePoint
 Cree una clase que defina la extensión del proyecto y el comportamiento de la nueva propiedad del proyecto. Para definir la nueva extensión de proyecto, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz. Implemente esta interfaz siempre que desee definir una extensión para un proyecto de SharePoint. Además, agregue <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] detectar y cargar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo al constructor del atributo.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Para definir la nueva propiedad de proyecto de SharePoint

1. Pegue el código siguiente en el archivo de código CustomProperty.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>Compilar la solución
 A continuación, compile la solución para asegurarse de que se compila sin errores.

#### <a name="to-build-the-solution"></a>Para compilar la solución

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Crear un paquete VSIX para implementar la extensión de propiedad de proyecto
 Para implementar la extensión de proyecto, use el Proyecto VSIX en la solución para crear un paquete VSIX. Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.

#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX

1. En **Explorador de soluciones**, abra el menú contextual del archivo source. Extension. vsixmanifest y, a continuación, elija el botón **abrir** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]abre el archivo en el diseñador de manifiestos. La información que aparece en la pestaña **metadatos** también aparece en las **extensiones y actualizaciones**. Todos los paquetes VSIX requieren el archivo Extension. vsixmanifest. Para obtener más información acerca de este archivo, vea [referencia de esquema de extensión VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. En el cuadro **Product Name** , escriba **Custom Project Property**.

3. En el cuadro **autor** , escriba **contoso**.

4. En el cuadro **Descripción** , escriba **una propiedad personalizada del proyecto de SharePoint que alterne la asignación de la carpeta de recursos images al proyecto**.

5. Elija la pestaña **activos** y, a continuación, elija el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

6. En la lista **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Este valor corresponde al elemento `MEFComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, vea [elemento MEFComponent (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. En la lista **origen** , elija el botón de opción **un proyecto en la solución actual** .

8. En la lista **proyecto** , elija **ProjectExtension**.

     Este valor identifica el nombre del ensamblado que se está compilando en el proyecto.

9. Elija **Aceptar** para cerrar el cuadro de diálogo **Agregar nuevo activo** .

10. En la barra de menús, elija **archivo**  >  **guardar todo** al finalizar y, a continuación, cierre el diseñador de manifiestos.

11. En la barra de menús, **Elija compilar compilar**  >  **solución**y, a continuación, asegúrese de que el proyecto se compila sin errores.

12. En **Explorador de soluciones**, abra el menú contextual del proyecto **ProjectExtensionPackage** y elija el botón **Abrir carpeta en el explorador de archivos** .

13. En el **Explorador de archivos**, abra la carpeta de resultados de compilación para el proyecto ProjectExtensionPackage y, a continuación, compruebe que la carpeta contiene un archivo denominado ProjectExtensionPackage. vsix.

     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.

## <a name="test-the-project-property"></a>Prueba de la propiedad del proyecto
 Ahora está listo para probar la propiedad personalizada del proyecto. Es más fácil depurar y probar la nueva extensión de propiedad de proyecto en una instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Esta instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se crea al ejecutar un VSIX u otro proyecto de extensibilidad. Después de depurar el proyecto, puede instalar la extensión en el sistema y, a continuación, continuar con la depuración y prueba en una instancia normal de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Para depurar y probar la extensión en una instancia experimental de Visual Studio

1. Reinicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenciales administrativas y, a continuación, abra la solución ProjectExtensionPackage.

2. Inicie una compilación de depuración del proyecto; para ello, elija la tecla **F5** o, en la barra de menús, elija **depurar**  >  **iniciar depuración**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]instala la extensión en el proyecto%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1.0 e inicia una instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. En la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , cree un proyecto de SharePoint para una solución de granja de servidores y use los valores predeterminados para los demás valores del asistente.

    1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

    2. En la parte superior del cuadro de diálogo **nuevo proyecto** , elija **.NET Framework 3,5** en la lista de versiones de la .NET Framework.

         Las extensiones de herramientas de SharePoint requieren características en esta versión de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. En el nodo **plantillas** , expanda el nodo **Visual C#** o **Visual Basic** , elija el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

    4. Elija la plantilla de **proyecto de SharePoint 2010** y, a continuación, escriba **ModuleTest** como nombre del proyecto.

4. En **Explorador de soluciones**, elija el nodo del proyecto **ModuleTest** .

     Aparece una nueva **carpeta de imágenes de asignación** de propiedades personalizadas en la ventana **propiedades** con un valor predeterminado de **false**.

5. Cambie el valor de esa propiedad a **true**.

     Se agrega una carpeta de recursos images al proyecto de SharePoint.

6. Vuelva a cambiar el valor de la propiedad a **false**.

     Si elige el botón **sí** en el cuadro de diálogo **eliminar la carpeta images?** , se eliminará la carpeta de recursos images del proyecto de SharePoint.

7. Cierre la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="see-also"></a>Consulte también
- [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Cómo: agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyectos de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Asociar datos personalizados con las extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
