---
title: Implementar una solución de VSTO con Windows Installer
titleSuffix: ''
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a6fd2824ae10ad36a7ed50250620e98575e9ea60
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585698"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Implementar una solución de VSTO con Windows Installer

## <a name="summary"></a>Resumen

Aprenda a implementar un complemento de Microsoft Visual Studio Tools para Office (VSTO) o una solución de nivel de documento mediante un proyecto de Instalador de Visual Studio.

Wouter van Vugt, asesor de código

Ted Pattison, grupo Ted Pattison

Microsoft actualizó este artículo con el permiso de los autores originales.

**Se aplica a:** Visual Studio Tools para Office, Microsoft Office Microsoft Visual Studio.

## <a name="overview"></a>Información general

Puede desarrollar una solución de VSTO e implementar la solución mediante un paquete de Windows Installer. En esta explicación se incluyen los pasos para implementar un complemento de Office sencillo.

## <a name="deployment-methods"></a>Métodos de implementación

ClickOnce se puede usar fácilmente para crear configuraciones para las soluciones y los complementos. Sin embargo, no puede instalar complementos que requieran privilegios administrativos, como los complementos de nivel de equipo.

Los complementos que requieren privilegios administrativos se pueden instalar mediante Windows Installer pero requiere más esfuerzo para crear el programa de instalación.

Para obtener información general sobre cómo implementar una solución de VSTO mediante ClickOnce, vea [implementar una solución de Office mediante ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Implementar soluciones de Office destinadas al tiempo de ejecución de VSTO

Los paquetes ClickOnce y Windows Installer deben realizar las mismas tareas rudimentarias al instalar una solución de Office.

1. Instale los componentes de requisitos previos en el equipo del usuario.
2. Implemente los componentes específicos de la solución.
3. En el caso de los complementos, cree entradas del registro.
4. Confíe en la solución para que pueda ejecutarse.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Componentes necesarios para los requisitos previos en el equipo de destino

Esta es la lista de software que se debe instalar en el equipo para ejecutar soluciones de VSTO:

- Microsoft Office 2010 o posterior.
- Microsoft .NET Framework 4 o posterior.
- Runtime de Microsoft Visual Studio 2010 Tools para Office.
  El motor en tiempo de ejecución proporciona un entorno que administra los complementos y las soluciones de nivel de documento. Una versión del motor en tiempo de ejecución se incluye en Microsoft Office pero puede que desee redistribuir una versión específica con el complemento.
- Los ensamblados de interoperabilidad primarios para Microsoft Office, si no está usando tipos de interoperabilidad incrustados.
- Los ensamblados de utilidades a los que hacen referencia los proyectos.

### <a name="specific-components-for-the-solution"></a>Componentes específicos de la solución

El paquete del instalador debe instalar estos componentes en el equipo del usuario:

- El Microsoft Office documento, si crea una solución de nivel de documento.
- El ensamblado de personalización y los ensamblados que requiere.
- Componentes adicionales, como archivos de configuración.
- El manifiesto de aplicación (. manifest).
- El manifiesto de implementación (. VSTO).

### <a name="registry-entries-for-add-ins"></a>Entradas del registro para complementos

Microsoft Office utiliza entradas del registro para buscar y cargar complementos. Estas entradas del registro deben crearse como parte del proceso de implementación. Para obtener más información sobre estas entradas del registro, vea [entradas del registro para complementos de VSTO](registry-entries-for-vsto-add-ins.md).

Los complementos de Outlook que muestran áreas de formulario personalizadas requieren entradas de registro adicionales que permiten identificar las áreas de formulario. Para obtener más información acerca de las entradas del registro, consulte [entradas del registro para las áreas de formulario de Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Las soluciones de nivel de documento no requieren ninguna entrada del registro. En su lugar, las propiedades dentro del documento se usan para buscar la personalización. Para obtener más información acerca de estas propiedades, vea [información general sobre las propiedades personalizadas del documento](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Confiar en la solución de VSTO

Para que se ejecute una personalización, la máquina debe confiar en una solución. El complemento puede ser de confianza si se firma el manifiesto con un certificado, se crea una relación de confianza con una lista de inclusión o se instala en una ubicación de confianza del equipo.

Para obtener más información sobre cómo obtener un certificado para firmar, vea [ClickOnce Deployment and Authenticode](../deployment/clickonce-and-authenticode.md). Para obtener más información sobre las soluciones de confianza, vea [confiar en soluciones de Office mediante listas de inclusión](trusting-office-solutions-by-using-inclusion-lists.md). Puede Agregar una entrada de la lista de inclusión con una acción personalizada en el archivo de Windows Installer. Para obtener más información acerca de la habilitación de la lista de inclusión, consulte [Cómo: configurar la seguridad](how-to-configure-inclusion-list-security.md)de la lista de inclusión.

Si no se utiliza ninguna de las opciones, se muestra al usuario un mensaje de confianza que les permite decidir si confiar en la solución.

Para obtener más información sobre la seguridad relacionada con las soluciones de nivel de documento, vea [conceder confianza a los documentos](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Creación de un instalador básico

Las plantillas de proyecto de instalación e implementación se incluyen con la extensión de [proyectos del instalador de Microsoft Visual Studio](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) que está disponible para su descarga.

Para crear un instalador para una solución de Office, estas tareas se deben realizar:

- Agregue los componentes de la solución de Office que se implementarán.
- En el caso de los complementos de nivel de aplicación, configure las claves del registro.
- Configure los componentes de requisitos previos para que se puedan instalar en los equipos de los usuarios finales.
- Configure las condiciones de inicio para comprobar que están disponibles los componentes de requisitos previos necesarios. Las condiciones de inicio se pueden usar para bloquear la instalación si no están instalados todos los requisitos previos necesarios.

El primer paso es crear el proyecto de instalación.

### <a name="to-create-the-addin-setup-project"></a>Para crear el proyecto de instalación de AddIn

1. Abra el proyecto de complemento de Office que desea implementar. En este ejemplo, vamos a usar un complemento de Excel denominado ExcelAddIn.
2. Con el proyecto de Office abierto, en el menú **archivo** , expanda **Agregar** y haga clic en **nuevo proyecto** para agregar un nuevo proyecto.
::: moniker range="=vs-2017"
3. En el cuadro de diálogo **Agregar nuevo proyecto** , expanda **otros tipos de proyectos** en **el panel tipos de proyecto** , expanda **instalación e implementación** y, a continuación, seleccione **instalador de Visual Studio**.
4. En el panel **plantillas** , seleccione **proyecto de instalación** en el grupo plantillas **instaladas de Visual Studio** .
::: moniker-end
::: moniker range="=vs-2019"
3. En el cuadro de diálogo **Agregar un nuevo proyecto** , seleccione la plantilla **proyecto de instalación** .
4. Haga clic en **Siguiente**.
::: moniker-end

5. En el cuadro **nombre** , escriba **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Haga clic en **abrir** para crear el nuevo proyecto de instalación.
::: moniker-end
::: moniker range="=vs-2019"
6. Haga clic en **crear** para crear el nuevo proyecto de instalación.
::: moniker-end

Visual Studio abre el explorador del sistema de archivos para el nuevo proyecto de instalación. El explorador de sistema de archivos permite agregar archivos al proyecto de instalación.

   ![Captura de pantalla del explorador del sistema de archivos para el proyecto de instalación](media/setup-project-figure-1.png)

   **Figura 1: explorador del sistema de archivos para el proyecto de instalación**

El proyecto de instalación debe implementar ExcelAddIn. Puede configurar el proyecto de instalación para esta tarea agregando el resultado del proyecto ExcelAddIn al proyecto de instalación.

### <a name="to-add-the-exceladdin-project-output"></a>Para agregar el resultado del proyecto ExcelAddIn

1. En el **Explorador de soluciones**, haga clic con el botón secundario en **OfficeAddInSetup**, haga clic en **Agregar** y luego en **resultados del proyecto**.
2. En el cuadro de diálogo **Agregar grupo de resultados del proyecto** , seleccione **ExcelAddIn** en la lista proyecto y **resultado principal**.
3. Haga clic en **Aceptar** para agregar el resultado del proyecto al proyecto de instalación.

    ![Captura de pantalla del cuadro de diálogo Agregar grupo de resultados del proyecto de instalación](media/setup-project-figure-2.png)

    **Figura 2: cuadro de diálogo del proyecto de instalación agregar grupo de resultados del proyecto**

El proyecto de instalación debe implementar el manifiesto de implementación y el manifiesto de aplicación. Agregue estos dos archivos al proyecto de instalación como archivos independientes de la carpeta de salida del proyecto ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Para agregar los manifiestos de implementación y de aplicación

1. En el **Explorador de soluciones**, haga clic con el botón secundario en **OfficeAddInSetup**, haga clic en **Agregar**y, a continuación, en **archivo**.
2. En el cuadro de diálogo **Agregar archivos** , navegue hasta el directorio de salida de **ExcelAddIn** . Normalmente, el directorio de salida es la subcarpeta de ** \\ versión bin** del directorio raíz del proyecto, según la configuración de compilación seleccionada.
3. Seleccione los archivos **ExcelAddIn. VSTO** y **ExcelAddIn.dll. manifest** y haga clic en **abrir** para agregar estos dos archivos al proyecto de instalación.

    ![Captura de pantalla de los manifiestos de aplicación e implementación en Explorador de soluciones](media/setup-project-figure-3.jpg)

    **Figura 3: manifiestos de aplicación y de implementación para el complemento en Explorador de soluciones**

La referencia a ExcelAddIn incluye todos los componentes que requiere ExcelAddIn. Estos componentes se deben excluir e implementar con paquetes de requisitos previos para permitir que se registren correctamente. Además, los términos de licencia de software deben mostrarse y aceptarse antes de que comience la instalación.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Para excluir las dependencias del proyecto ExcelAddIn

1. En el **Explorador de soluciones**, en el **nodo OfficeAddInSetup** , seleccione todos los elementos de dependencia debajo del elemento **dependencias detectadas** , excepto **Microsoft .NET Framework** o cualquier ensamblado que termine con ** \*.Utilities.dll**. Los ensamblados de utilidades están diseñados para implementarse junto con la aplicación.
2. Haga clic con el botón secundario en el grupo y seleccione **propiedades**.
3. En la ventana **propiedades** , cambie la propiedad **Exclude** a **true** para excluir los ensamblados dependientes del proyecto de instalación. Asegúrese de no excluir los ensamblados de utilidades.

    ![Captura de pantalla de Explorador de soluciones que muestra las dependencias que se van a excluir](media/setup-project-figure-4.jpg)

    **Figura 4: exclusión de las dependencias**

Puede configurar el paquete de Windows Installer para instalar los componentes de requisitos previos agregando un programa de instalación, también conocido como arranque. Este programa de instalación puede instalar los componentes de requisitos previos, un proceso denominado arranque.

En el caso de **ExcelAddIn**, estos requisitos previos deben instalarse antes de que el complemento pueda ejecutarse correctamente:

- Versión de Microsoft .NET Framework a la que se destina la solución de Office.
- Tiempo de ejecución de Microsoft Visual Studio Tools 2010 para Office.

Para configurar los componentes dependientes como requisitos previos

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **OfficeAddInSetup** y seleccione **propiedades**.
2. Aparece el cuadro de diálogo **páginas de propiedades de OfficeAddInSetup** .
3. Haga clic en el botón **requisitos previos** .
4. En el cuadro de diálogo requisitos previos, seleccione la versión correcta del .NET Framework y el motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office.

    ![Captura de pantalla del cuadro de diálogo requisitos previos](media/setup-project-figure-5.png)

    **Figura 5: cuadro de diálogo requisitos previos**

    > [!NOTE]
    >Algunos de los paquetes de requisitos previos configurados en el proyecto de instalación de Visual Studio dependen de la configuración de compilación seleccionada. Debe seleccionar los componentes de requisitos previos correctos para cada configuración de compilación que use.

Microsoft Office busca complementos mediante claves del registro. Las claves del \_ \_ subárbol del usuario HKEY actual se usan para registrar el complemento para cada usuario individual. Las claves del \_ \_ subárbol del equipo local HKEY se usan para registrar el complemento para todos los usuarios de la máquina. Para obtener más información acerca de las claves del registro, vea [entradas del registro para complementos de VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Para configurar el registro

1. En el **Explorador de soluciones**, haga clic con el botón secundario en **OfficeAddInSetup**.
2. Expanda **vista**.
3. Haga clic en **registro** para abrir la ventana del editor del registro.
4. En el editor **del registro (OfficeAddInSetup)** , expanda **HKEY \_ local \_ Machine** y **software**.
5. Elimine la clave ** \[ manufacturer \] **? que se encuentra en **HKEY \_ local \_ Machine \\ software**.
6. Expanda **HKEY \_ Current \_ User** y, a continuación, **software**.
7. Elimine la clave ** \[ del fabricante \] ** que se encuentra en **HKEY \_ Current \_ User \\ software**.
8. Para agregar las claves del registro para la instalación del complemento, haga clic con el botón secundario en la clave de **Hive usuario/equipo** , seleccione **nueva clave**. Use el **software** de texto como nombre de la nueva clave. Haga clic con el botón secundario en la clave de **software** recién creada y cree una nueva clave con el texto **Microsoft**.
9. Use un proceso similar para crear la jerarquía de claves completa necesaria para el registro del complemento:

    **Software de Hive de usuario/equipo \\ \\ Microsoft \\ Office \\ Excel \\ AddIns \\ clave samplecompany. ExcelAddIn**

    El nombre de la compañía se usa a menudo como prefijo del nombre del complemento para proporcionar exclusividad.

10. Haga clic con el botón secundario en la clave **clave samplecompany. ExcelAddIn** , seleccione **nuevo**y haga clic en **valor de cadena**. Use la **Descripción** de texto para el nombre.
11. Use este paso para agregar tres valores más:
    - **FriendlyName** de tipo **cadena**
    - **LoadBehavior** de tipo **DWORD**
    - **Manifiesto** de tipo **cadena**

12. Haga clic con el botón secundario en el valor **Descripción** en el editor del registro y haga clic en **ventana Propiedades**. En la **ventana Propiedades**, escriba **complemento de demostración de Excel** para la propiedad valor.
13. Seleccione la clave **FriendlyName** en el editor del registro. En la **ventana Propiedades**, cambie la propiedad **valor** a **complemento de demostración de Excel**.
14. Seleccione la clave **LoadBehavior** en el editor del registro. En la **ventana Propiedades**, cambie la propiedad **Value** a **3.** El valor 3 para LoadBehavior indica que el complemento se debe cargar en el inicio de la aplicación host. Para obtener más información sobre el comportamiento de carga, vea [entradas del registro para complementos de VSTO](registry-entries-for-vsto-add-ins.md).

15. Seleccione la clave de **manifiesto** en el editor del registro. En la **ventana Propiedades**, cambie la propiedad **valor** a **archivo:///[targetdir] ExcelAddIn. VSTO | vstolocal**

    ![Captura de pantalla del editor del registro](media/setup-project-figure-6.png)

    **Figura 6: configuración de claves del registro**

      El tiempo de ejecución de VSTO usa esta clave del registro para buscar el manifiesto de implementación. La macro [TARGETDIR] se reemplazará por la carpeta en la que está instalado el complemento. La macro incluirá el carácter \ final, por lo que el nombre de archivo del manifiesto de implementación debe ser ExcelAddIn. VSTO sin el carácter \.
      El postfijo **vstolocal** indica al tiempo de ejecución de VSTO que el complemento debe cargar desde esta ubicación en lugar de la caché ClickOnce. Si se quita este sufijo, el tiempo de ejecución copia la personalización en la caché de ClickOnce.

   >[!WARNING]
   >Debe tener mucho cuidado con el editor del registro en Visual Studio. Por ejemplo, si establece accidentalmente DeleteAtUninstall para la clave equivocada, podría eliminar una parte activa del registro, lo que dejaría al equipo del usuario en un estado incoherente, o incluso peor, roto.

las versiones de 64 bits de Office usarán el subárbol del registro de 64 bits para buscar complementos. Para registrar complementos en el subárbol del registro de 64 bits, la plataforma de destino del proyecto de instalación debe establecerse en solo 64 bits.

1. Seleccione el proyecto **OfficeAddInSetup** en el explorador de soluciones.
2. Vaya a la ventana **propiedades** y establezca la propiedad **targetplatform** en **x64**.

La instalación de un complemento para las versiones de Office de 32 y 64 bits le obligará a crear dos paquetes MSI independientes. Uno para 32 bits y otro para 64 bits.

  ![Captura de pantalla de la ventana Propiedades que muestra la plataforma de destino para registrar complementos con Office de 64 bits](media/setup-project-figure-7.jpg)

  **Figura 7: plataforma de destino para el registro de complementos con Office de 64 bits**

Si el paquete MSI se usa para instalar el complemento o la solución, puede instalar sin los requisitos previos necesarios que se estén instalando. Puede usar las condiciones de inicio en el archivo MSI para impedir que se instale el complemento si los requisitos previos no están instalados.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configurar una condición de inicio para detectar el tiempo de ejecución de VSTO

1. En el **Explorador de soluciones**, haga clic con el botón secundario en **OfficeAddInSetup**.
2. Expanda **vista**.
3. Haga clic en **condiciones de inicio**.
4. En el editor de **condiciones de inicio (OfficeAddInSetup)** , haga clic con el botón secundario en **requisitos en el equipo de destino**y, a continuación, haga clic en **Agregar condición de inicio del registro**. Esta condición de búsqueda puede buscar en el registro una clave que instale el tiempo de ejecución de VSTO. A continuación, el valor de la clave está disponible para las distintas partes del instalador a través de una propiedad con nombre. La condición de inicio utiliza la propiedad definida por la condición de búsqueda para comprobar un determinado valor.
5. En el editor de **condiciones de inicio (OfficeAddInSetup)** , seleccione la condición **de búsqueda Buscar RegistryEntry1** , haga clic con el botón derecho en la condición y seleccione **ventana Propiedades**.

6. En la ventana **Propiedades** , establezca estas propiedades:
   1. Establezca el valor de **(nombre)** para **Buscar el tiempo de ejecución de VSTO 2010**.
   2. Cambie el valor de la **propiedad** a **VSTORUNTIMEREDIST**.
   3. Establezca el valor de **RegKey** en **software \\ Microsoft \\ VSTO Runtime Setup \\ v4R**
   4. Deje la propiedad **raíz** establecida en **vsdrrHKLM**.
   5. Cambie la propiedad **Value** a **version**.

7. En el editor de **condiciones de inicio (OfficeAddInSetup)** , seleccione la condición de inicio **Condition1** , haga clic con el botón derecho en la condición y seleccione **ventana Propiedades**.
8. En la ventana Propiedades, establezca estas propiedades:
   1. Establezca el **(nombre)** para **comprobar la disponibilidad en tiempo de ejecución de VSTO 2010**.
   2. Cambiar el valor de la **condición** a **VSTORUNTIMEREDIST \> = "10.0.30319"**
   3. Deje la propiedad **InstallUrl** en blanco.
   4. Establecer el **mensaje** en **el tiempo de ejecución de Visual Studio 2010 Tools para Office no está instalado. Ejecute Setup.exe para instalar el complemento**.

        ![Captura de pantalla de la ventana Propiedades de la condición de inicio comprobar disponibilidad en tiempo de ejecución](media/setup-project-figure-8.jpg)

        **Figura 8: ventana Propiedades de la condición de inicio comprobar disponibilidad en tiempo de ejecución**

 La condición de inicio anterior comprueba explícitamente la presencia del tiempo de ejecución de VSTO cuando lo instala el paquete de programa previo.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configurar una condición de inicio para detectar el tiempo de ejecución de VSTO instalado por Office

1. En el editor de **condiciones de inicio (OfficeAddInSetup)** , haga clic con el botón secundario en **equipo de destino de búsqueda**y, a continuación, haga clic en **Agregar búsqueda de registro**.
2. Seleccione la condición **de búsqueda Buscar RegistryEntry1** , haga clic con el botón derecho en la condición y seleccione **ventana Propiedades**.
3. En la ventana **Propiedades** , establezca estas propiedades:
    1. Establezca el valor de **(nombre)** para **Buscar el tiempo de ejecución de VSTO de Office**.
    2. Cambie el valor de la **propiedad** a **OfficeRuntime**.
    3. Establezca el valor de **RegKey** en **software \\ Microsoft \\ VSTO Runtime Setup \\ V4**.
    4. Deje la propiedad **raíz** establecida en **vsdrrHKLM**.
    5. Cambie la propiedad **Value** a **version**.

4. En el editor de **condiciones de inicio (OfficeAddInSetup)** , seleccione la condición de inicio de la **disponibilidad en tiempo de ejecución de VSTO 2010** definida anteriormente, haga clic con el botón derecho en la condición y seleccione **ventana Propiedades**.

5. Cambie el valor de la propiedad **Condition** a **VSTORUNTIMEREDIST \> = "10.0.30319" o OFFICERUNTIME \> = "10.0.21022"**. Los números de versión puede ser diferentes en función de las versiones del tiempo de ejecución que requiera el complemento.

    ![Captura de pantalla de las ventanas de propiedades para la condición de inicio](media/setup-project-figure-9.jpg)
  
    **Figura 9: ventanas de propiedades para la condición comprobar la disponibilidad en tiempo de ejecución mediante Redist u Office Launch**

Si un complemento tiene como destino .NET Framework 4 o una versión más reciente, los tipos dentro de los ensamblados de interoperabilidad primarios (PIA) a los que se hace referencia se pueden incrustar en el ensamblado de VSTO.

Para comprobar si los tipos de interoperabilidad se van a incrustar en el complemento, siga estos pasos:

1. Expanda el nodo referencias en Explorador de soluciones
2. Seleccione una de las referencias de PIA, por ejemplo, **Office**.
3. Vea las ventanas de propiedades presionando F4 o seleccionando Propiedades en el menú contextual de ensamblados.
4. Compruebe el valor de la propiedad **incrustar tipos de interoperabilidad**.

Si el valor se establece en **true**, los tipos se incrustan y puede pasar a la sección [**para compilar el proyecto de instalación**](#to-build-the-setup-project) .

Para obtener más información, vea [equivalencia de tipos y tipos de interoperabilidad incrustados](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types) .

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Para configurar condiciones de inicio para detectar que para los PIA de Office

1. En el editor de **condiciones de inicio (OfficeAddInSetup)** , haga clic con el botón secundario en **requisitos en el equipo de destino**y, a continuación, **haga clic en agregar Windows Installer condición de inicio**. Esta condición de inicio busca un PIA de Office buscando el identificador de componente específico.
2. Haga clic con el botón derecho en **Buscar Component1** y haga clic en **ventana Propiedades** para mostrar las propiedades de la condición de inicio.
3. En la **ventana Propiedades**, establezca estas propiedades:

    1. Cambie el valor de la propiedad **(Name)** para **Buscar el Pia compartido de Office** .
    2. Cambie el valor de **ComponentID** a ID. de componente para el componente de Office que está usando. Puede encontrar la lista de identificadores de componente en la tabla siguiente, por ejemplo **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Cambie el valor de la propiedad **Property** a **HASSHAREDPIA**.

4. En el editor de **condiciones de inicio (OfficeAddInSetup)** , haga clic con el botón secundario en **Condition1** y haga clic en **ventana Propiedades** para mostrar las propiedades de la condición de inicio.

5. Cambie estas propiedades de **Condition1**:

    1. Cambie el **(nombre)** para **comprobar la disponibilidad de los PIA compartidos de Office**.
    2. Cambie la **condición** a **HASSHAREDPIA**.
    3. Deje el valor de **InstallUrl** en blanco.
    4. Cambiar el **mensaje** a **un componente necesario para interactuar con Excel no está disponible. Ejecute setup.exe**.

    ![Captura de pantalla de la ventana Propiedades de la condición de inicio comprobar el PIA compartido de Office](media/setup-project-figure-10.jpg)
  
    **Figura 10: ventana Propiedades de la condición de inicio comprobar el PIA compartido de Office**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Identificadores de componente de los ensamblados de interoperabilidad primarios para Microsoft Office

|Ensamblado de interoperabilidad primario|Office 2010|Office 2013|Office 2013 (64 bits)|Office 2016|Office 2016 (64 bits)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2,0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Etiqueta inteligente|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office compartido|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Captura de pantalla de las condiciones de inicio finales](media/setup-project-figure-11.jpg)

  **Figura 11: condiciones de inicio finales**

Puede refinar aún más las condiciones de inicio de la instalación de ExcelAddIn. Por ejemplo, puede ser útil comprobar si está instalada la aplicación de Office de destino real.

### <a name="to-build-the-setup-project"></a>Para compilar el proyecto de instalación

1. En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **OfficeAddInSetup** y haga clic en **compilar**.
2. Con el **Explorador de Windows**, navegue hasta el directorio de salida del proyecto **OfficeAddInSetup** y vaya a la carpeta Release or debug, dependiendo de la configuración de compilación seleccionada. Copie todos los archivos de la carpeta a una ubicación a la que puedan tener acceso los usuarios.

Para probar la instalación de ExcelAddIn

1. Navegue hasta la ubicación donde copió **OfficeAddInSetup** .
2. Haga doble clic en el archivo de setup.exe para instalar el complemento **OfficeAddInSetup** . Acepte los términos de licencia de software que aparecen y complete el Asistente para la instalación para instalar el complemento en el equipo del usuario.

La solución de Office para Excel debe instalarse y ejecutarse desde la ubicación especificada durante la instalación.

## <a name="additional-requirements-for-document-level-solutions"></a>Requisitos adicionales para las soluciones de nivel de documento

La implementación de soluciones de nivel de documento requiere unos pasos de configuración diferentes en el proyecto de instalación de Windows Installer.

Esta es una lista de los pasos básicos necesarios para implementar una solución de nivel de documento:

- Cree el proyecto de instalación de Visual Studio.
- Agregue el resultado principal de la solución de nivel de documento. La salida principal también incluye el documento Microsoft Office.
- Agregue los manifiestos de implementación y de aplicación como archivos sueltos.
- Excluya los componentes dependientes del paquete del instalador (excepto los ensamblados de utilidades).
- Configure los paquetes de requisitos previos.
- Configurar condiciones de inicio.
- Compile el proyecto de instalación y copie los resultados en la ubicación de implementación.
- Implemente la solución de nivel de documento en el equipo del usuario. para ello, ejecute el programa de instalación de.
- Actualice las propiedades de documento personalizadas si es necesario.

### <a name="changing-the-location-of-the-deployed-document"></a>Cambiar la ubicación del documento implementado

Las propiedades dentro de un documento de Office se usan para buscar soluciones de nivel de documento. Si el documento se instala en la misma carpeta que el ensamblado de VSTO, no se requieren cambios. Sin embargo, si se instala en una carpeta diferente, será necesario actualizar estas propiedades durante la instalación.

Para obtener más información acerca de estas propiedades de documento, vea [información general sobre las propiedades personalizadas del documento](custom-document-properties-overview.md).

Para cambiar estas propiedades, debe usar una acción personalizada durante la instalación.

En el ejemplo siguiente se usa una solución de nivel de documento denominada ExcelWorkbookProject y un proyecto de instalación denominado ExcelWorkbookSetup. El proyecto ExcelWorkbookSetup se configura con los mismos pasos descritos anteriormente, excepto para establecer las claves del registro.

Para agregar el proyecto de acción personalizada a la solución de Visual Studio

1. Agregue un nuevo proyecto de consola de .NET a la solución haciendo clic con el botón derecho en el **proyecto de implementación de documentos de Office** en el **Explorador de soluciones**
2. Expanda **Agregar** y haga clic en **nuevo proyecto**.
3. Seleccione la plantilla aplicación de consola y asigne al proyecto el nombre **AddCustomizationCustomAction**.

    ![Captura de pantalla del Explorador de soluciones AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figura 12: Explorador de soluciones AddCustomizationCustomAction**

4. Agregue una referencia a estos ensamblados:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft. VisualStudio. Tools. Applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Copie este código en Program.cs o Program. VB.

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Para agregar la personalización al documento, debe tener el identificador de la solución de nivel de documento de VSTO. Este valor se recupera del archivo de proyecto de Visual Studio.

Para recuperar el identificador de la solución

1. En el menú **compilar** , haga clic en **compilar solución** para compilar la solución de nivel de documento y agregar la propiedad ID. de solución al archivo de proyecto.
2. En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto de nivel de documento **ExcelWorkbookProject**
3. Haga clic en **UnloadProject** para acceder al archivo de proyecto desde Visual Studio.

    ![Captura de pantalla de Explorador de soluciones descargar la solución de documento de Excel](media/setup-project-figure-16.jpg)

    **Figura 13: descarga de la solución de documento de Excel**

4. En el **Explorador de soluciones**, haga clic con el botón secundario en **ExcelWorkbookProject** y haga clic en **EditExcelWorkbookProject. vbproj** o en **Editar ExcelWorkbookProject. csproj**.
5. En el editor **ExcelWorkbookProject** , busque el elemento **SolutionID** dentro del elemento **PropertyGroup** .
6. Copie el valor GUID de este elemento.

    ![Recuperando SolutionID](media/setup-project-figure-17.jpg)

    **Figura 14: recuperación del SolutionID**

7. En el **Explorador de soluciones**, haga clic con el botón secundario en **ExcelWorkbookProject** y haga clic en **volver a cargar el proyecto**.
8. Haga clic en **sí** en el cuadro de diálogo que aparece para cerrar el editor de **ExcelWorkbookProject** .
9. El **identificador** de la solución se usará en la acción de instalación personalizada.

El último paso es configurar la acción personalizada para los pasos de **instalación** y **desinstalación** .

### <a name="to-configure-the-setup-project"></a>Para configurar el proyecto de instalación

1. En el **Explorador de soluciones**, haga clic con el botón secundario en **ExcelWorkbookSetup**, expanda **Agregar** y haga clic en **resultado del proyecto**.
2. En el cuadro de diálogo **Agregar grupo de resultados del proyecto** , en la lista **proyecto** , haga clic en **AddCustomizationCustomAction**.
3. Seleccione **resultado principal** y haga clic en **Aceptar** para cerrar el cuadro de diálogo y agregar el ensamblado que contiene la acción personalizada al proyecto de instalación.

    ![Captura de pantalla de la acción personalizada manifiesto de documento: agregar grupo de resultados del proyecto](media/setup-project-figure-18.jpg)

    **Figura 15: acción personalizada del manifiesto del documento-agregar grupo de resultados del proyecto**

4. En el **Explorador de soluciones**, haga clic con el botón secundario en **ExcelWorkbookSetup**.
5. Expanda **Ver** y haga clic en **acciones personalizadas**.
6. En el editor de **acciones personalizadas (ExcelWorkbookSetup)** , haga clic con el botón secundario en **acciones personalizadas** y haga clic en **Agregar acción personalizada**.
7. En el cuadro de diálogo **Seleccionar elemento del proyecto** , en la lista **Buscar en** , haga clic en carpeta de la **aplicación**. Seleccione **resultado principal de AddCustomizationCustomAction (activo)** y haga clic en **Aceptar** para agregar la acción personalizada al paso de instalación.
8. En el **nodo instalar**, haga clic con el botón secundario en **resultado principal de AddCustomizationCustomAction (activo)** y haga clic en **cambiar nombre**. Asigne a la acción personalizada el nombre de **copia de mis documentos y adjunte la personalización**.
9. En el **nodo desinstalación**, haga clic con el botón secundario en **resultado principal de AddCustomizationCustomAction (activo)** y haga clic en **cambiar nombre**. Asigne a la acción personalizada el nombre **quitar documento de la carpeta documentos**.

    ![Captura de pantalla de la ventana acciones personalizadas del manifiesto del documento](media/setup-project-figure-19.jpg)

    **Figura 16: acciones personalizadas del manifiesto del documento**

10. En el editor de **acciones personalizadas (ExcelWorkbookSetup)** , haga clic con el botón secundario en **copiar documento en mis documentos y adjuntar personalización** y haga clic en la **ventana Propiedades**.
11. En la ventana **propiedades** de **CustomActionData** , escriba la ubicación del archivo dll de personalización, el manifiesto de implementación y la ubicación del documento Microsoft Office. También se necesita el SolutionID.
12. Si desea registrar los errores de instalación en un archivo, incluya un parámetro LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Captura de pantalla de la acción personalizada para copiar el documento en mis documentos ventana Propiedades](media/setup-project-figure-20.jpg)

    **Figura 17: acción personalizada para copiar un documento en mis documentos**

13. La acción personalizada para desinstalar necesita el nombre del documento, que puede proporcionar mediante el mismo parámetro documentLocation en el **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compile e implemente el proyecto **ExcelWorkbookSetup** .
15. Buscar en la carpeta **Mis documentos** y abrir el archivo de ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Recursos adicionales

[Cómo: instalar el motor en tiempo de ejecución de Visual Studio Tools para Office](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[ensamblados de interoperabilidad primarios de Office](office-primary-interop-assemblies.md)

[Entradas del registro para complementos de VSTO](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Especificar áreas de formulario en el registro de Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Acerca de los autores

Wouter van Vugt es un MVP de Microsoft con tecnologías Open XML de Office y un consultor independiente que se centra en la creación de Business Applications de Office (OBA) con SharePoint, Microsoft Office y tecnologías de .NET relacionadas.
Wouter es un colaborador frecuente de sitios de la comunidad de desarrolladores, como [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Ha publicado varias notas del producto y artículos, así como un libro disponible en la línea titulada Open XML: libro electrónico explicado.
Wouter es el fundador de Code-Counsel, una empresa holandesa que se centra en la entrega de contenido técnico de vanguardia a través de una variedad de canales. Para obtener más información acerca de Wouter, lea este blog.

Ted Pattison es un MVP de SharePoint, autor, instructor y el fundador del grupo Ted Pattison. En el período de 2005, Ted fue contratado por el grupo de aprendizaje de la plataforma de desarrollo de Microsoft para crear el plan de estudios de entrenamiento de desarrollo ascendente para Windows SharePoint Services 3,0 y Microsoft Office SharePoint Server 2007. Desde ese momento, Ted se ha centrado totalmente en educar a los desarrolladores profesionales en las tecnologías de SharePoint 2007. Ted ha terminado de escribir un libro para Microsoft Press titulado dentro de Windows SharePoint Services 3,0 que se centra en el uso de SharePoint como plataforma de desarrollo para la creación de soluciones empresariales. Ted también escribe una columna centrada en el desarrollador de MSDN Magazine titulada espacio de oficina.
