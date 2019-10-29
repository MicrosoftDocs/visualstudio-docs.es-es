---
title: 'Tutorial: extender un tipo de elemento de proyecto de SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 69ec79a613a2bcc50c47ea4d6b66516f75f1fbd6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983795"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Tutorial: extender un tipo de elemento de proyecto de SharePoint
  Puede utilizar el elemento de proyecto **modelo de conectividad a datos profesionales** para crear un modelo para el servicio de conectividad a datos profesionales (BDC) en SharePoint. De forma predeterminada, al crear un modelo utilizando este elemento de proyecto, los datos del modelo no se muestran a los usuarios. Por esta razón debe crear una lista externa en SharePoint que permita a los usuarios ver los datos.

 En este tutorial, creará una extensión para el elemento de proyecto **modelo de conectividad a datos profesionales** . Los desarrolladores pueden utilizar la extensión para crear una lista externa en sus proyectos que muestre los datos en el modelo BDC. En este tutorial se muestran las siguientes tareas:

- Crear una extensión Visual Studio que realiza dos tareas principales:

  - Genera una lista externa que muestra los datos en un modelo BDC. La extensión utiliza el modelo de objetos para que el sistema de proyectos de SharePoint genere un archivo *Elements. XML* que defina la lista. También agrega el archivo al proyecto para que se implemente junto con el modelo BDC.

  - Agrega un elemento de menú contextual a los elementos de proyecto de **modelo de conectividad a datos profesionales** en **Explorador de soluciones**. Los desarrolladores pueden hacer clic en este elemento de menú para generar una lista externa para el modelo BDC.

- Compilar un paquete de extensión de Visual Studio (VSIX) para implementar el ensamblado de la extensión.

- Probar la extensión.

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:

- Ediciones compatibles de Microsoft Windows, SharePoint y Visual Studio.

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. En este tutorial se usa la plantilla de **Proyecto VSIX** en el SDK para crear un paquete VSIX para implementar el elemento de proyecto. Para obtener más información, vea [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  El conocimiento de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial.

- El servicio BDC de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Para obtener más información, consulte [arquitectura de BDC](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14)).

- El esquema XML de los modelos BDC. Para obtener más información, vea [infraestructura del modelo BDC](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14)).

## <a name="create-the-projects"></a>Crear los proyectos
 Para completar este tutorial, debe crear dos proyectos:

- Un proyecto VSIX para crear el paquete VSIX e implementar la extensión de elemento de proyecto.

- Un proyecto de biblioteca de clases que implemente la extensión de elemento de proyecto.

  Comience el tutorial creando ambos proyectos.

#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX

1. Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **nuevo proyecto** , expanda los nodos **Visual C#**  o **Visual Basic** y, a continuación, elija el nodo **extensibilidad** .

    > [!NOTE]
    > El nodo **extensibilidad** solo está disponible si instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.

4. En la lista que se encuentra en la parte superior del cuadro de diálogo **nuevo proyecto** , elija **.NET Framework 4,5**.

     Las extensiones de herramientas de SharePoint requieren características de esta versión de .NET Framework.

5. Elija la plantilla de **Proyecto VSIX** .

6. En el cuadro **nombre** , escriba **GenerateExternalDataLists**y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **GenerateExternalDataLists** a **Explorador de soluciones**.

7. Si el archivo source. Extension. vsixmanifest no se abre automáticamente, abra el menú contextual en el proyecto GenerateExternalDataLists y, a continuación, elija **abrir** .

8. Compruebe que el archivo source.extension.vsixmanifest tenga una entrada que no esté en blanco (escriba Contoso) para el campo Autor, guarde el archivo y ciérrelo.

#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto

1. En **Explorador de soluciones**, abra el menú contextual del nodo de la solución **GenerateExternalDataLists** , elija **Agregar**y, a continuación, elija **nuevo proyecto**.

2. En el cuadro de diálogo **Agregar nuevo proyecto** , expanda los nodos  **C# visual** o **Visual Basic** y, a continuación, elija el nodo **Windows** .

3. En la lista de la parte superior del cuadro de diálogo, elija **.NET Framework 4,5**.

4. En la lista de plantillas de proyecto, elija **biblioteca de clases**.

5. En el cuadro **nombre** , escriba **BdcProjectItemExtension**y elija el botón **Aceptar** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **BdcProjectItemExtension** a la solución y abre el archivo de código predeterminado Class1.

6. Elimine el archivo de código Class1 del proyecto.

## <a name="configure-the-extension-project"></a>Configurar el proyecto de extensión
 Antes de escribir el código para crear la extensión de elemento de proyecto, tiene que agregar los archivos de código y las referencias de ensamblado al proyecto de extensión.

#### <a name="to-configure-the-project"></a>Para configurar el proyecto

1. En el proyecto BdcProjectItemExtension, agregue dos archivos de código que tienen los siguientes nombres:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Elija el proyecto BdcProjectItemExtension y, a continuación, en la barra de menús, elija **proyecto** > **Agregar referencia**.

3. En el nodo **ensamblados** , elija el nodo **Framework** y active la casilla de cada uno de los siguientes ensamblados:

    - System.ComponentModel.Composition

    - WindowsBase

4. En el nodo **ensamblados** , elija el nodo **extensiones** y, a continuación, active la casilla correspondiente al siguiente ensamblado:

    - Microsoft.VisualStudio.SharePoint

5. Elija el botón **Aceptar** .

## <a name="define-the-project-item-extension"></a>Definir la extensión del elemento de proyecto
 Cree una clase que defina la extensión para el elemento de proyecto **modelo de conectividad a datos profesionales** . Para definir la extensión, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>. Implemente esta interfaz para extender un tipo existente de elemento de proyecto todas las veces que desee.

#### <a name="to-define-the-project-item-extension"></a>Para definir la extensión del elemento de proyecto

1. Pegue el código siguiente en el archivo de código ProjectItemExtension.

    > [!NOTE]
    > Tras agregar este código, el proyecto tendrá algunos errores de compilación. Estos errores desaparecerán al agregar código en pasos posteriores.

     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]

## <a name="create-the-external-data-lists"></a>Crear las listas de datos externos
 Agregue una definición parcial de la clase `GenerateExternalDataListsExtension` que cree una lista de datos externa para cada entidad del modelo BDC. Para crear la lista de datos externos, este código lee primero los datos de entidad del modelo BDC mediante el análisis de los datos XML del archivo del modelo BDC. A continuación, crea una instancia de la lista basada en el modelo BDC y la agrega al proyecto.

#### <a name="to-create-the-external-data-lists"></a>Para crear las listas de datos externas

1. Pegue el código siguiente en el archivo de código GenerateExternalDataLists.

     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]

## <a name="checkpoint"></a>Punto de control
 En este punto del tutorial, todo el código de la extensión del elemento de proyecto está en el proyecto. Compile la solución para asegurarse de que el proyecto se compila sin errores.

#### <a name="to-build-the-solution"></a>Para compilar la solución

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Crear un paquete VSIX para implementar la extensión de elemento de proyecto
 Para implementar la extensión, utilice el proyecto VSIX en la solución para crear un paquete VSIX. Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.

#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX

1. En **Explorador de soluciones**, abra el menú contextual del archivo source. Extension. vsixmanifest en el proyecto GenerateExternalDataLists y, a continuación, elija **abrir**.

     Visual Studio abre el archivo en el editor de manifiestos. El archivo source.extension.vsixmanifest es la base del archivo extension.vsixmanifest que requieren todos los paquetes VSIX. Para obtener más información acerca de este archivo, vea [referencia de esquema de extensión VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. En el cuadro **Product Name** , escriba **external Data List generator**.

3. En el cuadro **autor** , escriba **contoso**.

4. En el cuadro **Descripción** , escriba **una extensión para los elementos de proyecto de modelo de conectividad a datos profesionales que se pueden usar para generar listas de datos externos**.

5. En la pestaña **activos** del editor, elija el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nuevo activo** .

6. En la lista **tipo** , elija **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Este valor corresponde al elemento `MefComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, vea [elemento MEFComponent (esquema VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. En la lista **origen** , elija **un proyecto en la solución actual**.

8. En la lista **proyecto** , elija **BdcProjectItemExtension**y, a continuación, elija el botón **Aceptar** .

9. En la barra de menús, elija **Compilar** > **Compilar solución**.

10. Asegúrese de que el proyecto se compila y se crea sin errores.

11. Asegúrese de que la carpeta de salida de la compilación del proyecto GenerateExternalDataLists contiene ahora el archivo GenerateExternalDataLists.vsix.

     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.

## <a name="test-the-project-item-extension"></a>Probar la extensión de elemento de proyecto
 Ya puede probar la extensión de elemento de proyecto. Primero, empiece a depurar el proyecto de extensión en la instancia experimental de Visual Studio. A continuación, utilice la extensión en la instancia experimental de Visual Studio para generar una lista externa para un modelo BDC. Finalmente, abra la lista externa en el sitio de SharePoint para comprobar que funciona según lo esperado.

#### <a name="to-start-debugging-the-extension"></a>Para comenzar a depurar la extensión

1. Si es necesario, reinicie Visual Studio con credenciales administrativas y, a continuación, abra la solución GenerateExternalDataLists.

2. En el proyecto BdcProjectItemExtension, abra el archivo de código ProjectItemExtension y, a continuación, agregue un punto de interrupción a la línea de código en el método `Initialize`.

3. Abra el archivo de código GenerateExternalDataLists y, a continuación, agregue un punto de interrupción a la primera línea de código en el método `GenerateExternalDataLists_Execute`.

4. Para iniciar la depuración, elija la tecla **F5** o, en la barra de menús, elija **depurar** > **iniciar depuración**.

     Visual Studio instala la extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1 .0 e inicia una instancia experimental de Visual Studio. Probará el elemento de proyecto en esta instancia de Visual Studio.

#### <a name="to-test-the-extension"></a>Para probar la extensión

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **archivo** > **nuevo** > **proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **plantillas** , expanda el nodo  **C# visual** , expanda el nodo **SharePoint** y, a continuación, elija **2010**.

3. En la lista de la parte superior del cuadro de diálogo, asegúrese de que está seleccionado **.NET Framework 3,5** . Los proyectos de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requieren esta versión de .NET Framework.

4. En la lista de plantillas de proyecto, elija **proyecto de SharePoint 2010**.

5. En el cuadro **nombre** , escriba **SharePointProjectTestBDC**y elija el botón **Aceptar** .

6. En el Asistente para la personalización de SharePoint, escriba la dirección URL del sitio que desea usar para la depuración, elija **implementar como solución de granja de servidores**y elija el botón **Finalizar** .

7. Abra el menú contextual del proyecto SharePointProjectTestBDC, elija **Agregar**y, a continuación, elija **nuevo elemento**.

8. En el cuadro de diálogo **Agregar newitem-SharePointProjectTestBDC** , expanda el nodo de idioma instalado, expanda el nodo **SharePoint** .

9. Elija el nodo **2010** y, a continuación, elija la plantilla **modelo de conectividad a datos profesionales (solo solución de granja)** .

10. En el cuadro **nombre** , escriba **TestBDCModel**y, a continuación, elija el botón **Agregar** .

11. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció anteriormente en el método `Initialize` del archivo de código ProjectItemExtension.

12. En la instancia detenida de Visual Studio, elija la tecla **F5** o, en la barra de menús, elija **depurar** > **continuar** para continuar depurando el proyecto.

13. En la instancia experimental de Visual Studio, elija la tecla **F5** o, en la barra de menús, elija **depurar** > **iniciar depuración** para compilar, implementar y ejecutar el proyecto **TestBDCModel** .

     El explorador web se abre en la página predeterminada del sitio de SharePoint que se especifica para la depuración.

14. Compruebe que la sección **listas** del área Inicio rápido todavía no contiene una lista basada en el modelo BDC predeterminado en el proyecto. Primero debe crear una lista de datos externa mediante la interfaz de usuario de SharePoint o la extensión de elemento de proyecto.

15. Cierre el explorador web.

16. En la instancia de Visual Studio que tiene abierto el proyecto TestBDCModel, abra el menú contextual del nodo **TestBDCModel** en **Explorador de soluciones**y, a continuación, elija **generar lista de datos externos**.

17. Compruebe que el código de la otra instancia de Visual Studio se detiene en el punto de interrupción que estableció en el método `GenerateExternalDataLists_Execute`. Elija la tecla **F5** o, en la barra de menús, elija **depurar** > **continuar** para continuar depurando el proyecto.

18. La instancia experimental de Visual Studio agrega una instancia de lista denominada **Entity1DataList** al proyecto TestBDCModel y la instancia también genera una característica denominada **característica2** para la instancia de lista.

19. Elija la tecla **F5** o, en la barra de menús, elija **depurar** > **iniciar depuración** para compilar, implementar y ejecutar el proyecto TestBDCModel.

     El explorador web se abre en la página predeterminada del sitio de SharePoint que se usa para depurar.

20. En la sección **listas** del área Inicio rápido, elija la lista **Entity1DataList** .

21. Compruebe que la lista contiene columnas denominadas Identificador1 y Mensaje, además de un elemento con un valor Identificador1 de 0 y un valor Mensaje de Hola a todos.

     La plantilla de proyecto **modelo de conectividad a datos profesionales** genera el modelo BDC predeterminado que proporciona todos estos datos.

22. Cierre el explorador web.

## <a name="clean-up-the-development-computer"></a>Limpiar el equipo de desarrollo
 Después de probar la extensión de elemento de proyecto, quite la lista externa y modelo BDC del sitio de SharePoint y quite la extensión de elemento de proyecto de Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Para quitar la lista de datos externa del sitio de SharePoint

1. En el área Inicio rápido del sitio de SharePoint, elija la lista **Entity1DataList** .

2. En la cinta de opciones del sitio de SharePoint, elija la pestaña **lista** .

3. En la pestaña **lista** , en el grupo **configuración** , elija **configuración**de la lista.

4. En **permisos y administración**, elija **eliminar esta lista**y, a continuación, haga clic en **Aceptar** para confirmar que desea enviar la lista a la papelera de reciclaje.

5. Cierre el explorador web.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Para quitar el modelo BDC del sitio de SharePoint

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **Compilar** > **retirar**.

     Visual Studio quita el modelo BDC del sitio de SharePoint.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Para quitar la extensión del elemento de proyecto de Visual Studio

1. En la instancia experimental de Visual Studio, en la barra de menús, elija **herramientas** > **extensiones y actualizaciones**.

     Se abre el cuadro de diálogo **Extensiones y actualizaciones**.

2. En la lista de extensiones, elija **generador de lista de datos externos**y, a continuación, elija el botón **desinstalar** .

3. En el cuadro de diálogo que aparece, elija **sí** para confirmar que desea desinstalar la extensión.

4. Elija **reiniciar ahora** para completar la desinstalación.

5. Cierre ambas instancias de Visual Studio (la instancia experimental y la instancia en la que se abre la solución GenerateExternalDataLists).

## <a name="see-also"></a>Vea también
- [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
