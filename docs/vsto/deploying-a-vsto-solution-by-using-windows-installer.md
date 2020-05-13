---
title: Implementación de una solución de Visual Studio Tools para Office con Windows Installer
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
ms.openlocfilehash: 46bfa808cbf99e942d7aadd2802f51eecfcefae8
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444911"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Implementación de una solución de Visual Studio Tools para Office con Windows Installer

## <a name="summary"></a>Resumen

Obtenga información sobre cómo implementar un complemento de Microsoft Visual Studio Tools para Office (VSTO) o una solución de nivel de documento mediante un proyecto de Visual Studio Installer.

Wouter van Vugt, Consejero del Código

Ted Pattison, Grupo Ted Pattison

Este artículo fue actualizado por Microsoft con el permiso de los autores originales.

**Se aplica a:** Visual Studio Tools para Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Información general

Puede desarrollar una solución VSTO e implementar la solución mediante un paquete de Windows Installer. Esta discusión incluye los pasos para implementar un complemento de Office simple.

## <a name="deployment-methods"></a>Métodos de implementación

ClickOnce clickOnce se puede usar fácilmente para crear configuraciones para sus complementos y soluciones. Sin embargo, no puede instalar complementos que requieran privilegios administrativos, como complementos de nivel de máquina.

Los complementos que requieren privilegios administrativos se pueden instalar mediante Windows Installer, pero requieren más esfuerzo para crear la instalación.

Para obtener información general sobre cómo implementar una solución VSTO mediante ClickOnce, vea Implementar una solución de [Office mediante ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Implementación de soluciones de Office destinadas al tiempo de ejecución de VSTO

Los paquetes ClickOnce y Windows Installer deben realizar las mismas tareas rudimentarias al instalar una solución de Office.

1. Instale los componentes de requisitos previos en el equipo del usuario.
2. Implemente los componentes específicos para la solución.
3. Para complementos, cree entradas de registro.
4. Confíe en la solución para permitir que se ejecute.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Componentes de requisitos previos necesarios en el equipo de destino

Esta es la lista de software que debe instalarse en el equipo para ejecutar soluciones VSTO:

- Microsoft Office 2010 o posterior.
- Microsoft .NET Framework 4 o posterior.
- Runtime de Microsoft Visual Studio 2010 Tools para Office.
  El tiempo de ejecución proporciona un entorno que administra complementos y soluciones de nivel de documento. Una versión de Tiempo de Ejecución se incluye con Microsoft Office, pero es posible que desee redistribuir una versión específica con el complemento.
- Los ensamblados de interoperabilidad primarios para Microsoft Office, si no usa tipos de interoperabilidad incrustados.
- Cualquier ensamblado de utilidades al que hacen referencia los proyectos.

### <a name="specific-components-for-the-solution"></a>Componentes específicos para la solución

El paquete del instalador debe instalar estos componentes en el equipo del usuario:

- El documento de Microsoft Office, si crea una solución de nivel de documento.
- El ensamblado de personalización y los ensamblados que requiere.
- Componentes adicionales, como archivos de configuración.
- El manifiesto de aplicación (.manifest).
- El manifiesto de implementación (.vsto).

### <a name="registry-entries-for-add-ins"></a>Entradas del Registro para Complementos

Microsoft Office usa entradas del Registro para buscar y cargar complementos. Estas entradas del registro deben crearse como parte del proceso de implementación. Para obtener más información acerca de estas entradas del Registro, vea [Entradas del Registro para complementos VSTO](registry-entries-for-vsto-add-ins.md).

Los complementos de Outlook que muestran regiones de formulario personalizadas requieren entradas de registro adicionales que permitan identificar las regiones de formulario. Para obtener más información acerca de las entradas del Registro, vea [Entradas del Registro para regiones](registry-entries-for-vsto-add-ins.md#OutlookEntries)de formulario de Outlook .

Las soluciones de nivel de documento no requieren ninguna entrada de registro. En su lugar, las propiedades dentro del documento se utilizan para buscar la personalización. Para obtener más información acerca de estas propiedades, vea Información general sobre propiedades de [documento personalizadas](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Confiar en la solución VSTO

Para que se ejecute una personalización, el equipo debe confiar en una solución. El complemento se puede confiar firmando el manifiesto con un certificado, creando una relación de confianza con una lista de inclusión o instalándolo en una ubicación de confianza en el equipo.

Para obtener más información acerca de cómo obtener un certificado para la firma, vea [ClickOnce Deployment and Authenticode](../deployment/clickonce-and-authenticode.md). Para obtener más información acerca de la confianza en las soluciones, vea Confiar en soluciones de Office mediante listas de [inclusión](trusting-office-solutions-by-using-inclusion-lists.md). Puede agregar una entrada de lista de inclusión con una acción personalizada en el archivo de Windows Installer. Para obtener más información acerca de cómo habilitar la lista de inclusión, vea [Cómo: Configurar la](how-to-configure-inclusion-list-security.md)seguridad de la lista de inclusión .

Si no se utiliza ninguna opción, se muestra un mensaje de confianza al usuario para que decida si desea confiar en la solución.

Para obtener más información acerca de la seguridad relacionada con las soluciones de nivel de documento, consulte [Concesión de confianza a documentos](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Creación de un instalador básico

Las plantillas de proyecto de instalación e implementación se incluyen con la extensión Proyectos de instalador de [Microsoft Visual Studio](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) que está disponible para su descarga.

Para crear un instalador para una solución de Office, estas tareas deben realizarse:

- Agregue los componentes de la solución de Office que se implementarán.
- Para complementos de nivel de aplicación, configure las claves del Registro.
- Configure los componentes de requisitos previos para que se puedan instalar en los equipos de los usuarios finales.
- Configure las condiciones de lanzamiento para comprobar que los componentes de requisitos previos necesarios están disponibles. Las condiciones de lanzamiento se pueden utilizar para bloquear la instalación si no se instalan todos los requisitos previos necesarios.

El primer paso es crear el proyecto de instalación.

### <a name="to-create-the-addin-setup-project"></a>Para crear el proyecto de instalación de AddIn

1. Abra el proyecto de complemento de Office que desea implementar. Para este ejemplo, estamos usando un complemento de Excel llamado ExcelAddIn.
2. Con el proyecto de Office abierto, en el **archivo** menú, expanda **agregar** y haga clic en **nuevo proyecto** para agregar un nuevo proyecto.
::: moniker range="=vs-2017"
3. En el cuadro de diálogo **Agregar nuevo proyecto,** expanda **Otros tipos de proyecto** en el panel **Tipos** de proyecto, expanda Instalación **e implementación** y, a continuación, seleccione Instalador de **Visual Studio**.
4. En **el** plantillas panel, seleccione **proyecto** de instalación desde el visual visual que se muestra el grupo de plantillas instaladas de **Visual Studio.**
::: moniker-end
::: moniker range="=vs-2019"
3. En el cuadro de diálogo **Agregar un nuevo proyecto,** seleccione la plantilla **Configurar proyecto.**
4. Haga clic en **Next**.
::: moniker-end

5. En el cuadro **Nombre** , escriba **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Haga clic en **Abrir** para crear el nuevo proyecto de instalación.
::: moniker-end
::: moniker range="=vs-2019"
6. Haga clic en **Crear** para crear el nuevo proyecto de instalación.
::: moniker-end

Visual Studio abre el Explorador del sistema de archivos para el nuevo proyecto de instalación. El Explorador del sistema de archivos le permite agregar archivos al proyecto de instalación.

   ![Captura de pantalla del Explorador del sistema de archivos para el proyecto de configuración](media/setup-project-figure-1.png)

   **Figura 1: Explorador del sistema de archivos para el proyecto de instalación**

El proyecto de instalación debe implementar ExcelAddIn. Puede configurar el proyecto de instalación para esta tarea agregando la salida del proyecto ExcelAddIn al proyecto de instalación.

### <a name="to-add-the-exceladdin-project-output"></a>Para agregar la salida del proyecto ExcelAddIn

1. En el Explorador de **soluciones**, haga clic con el botón secundario en **OfficeAddInSetup**, haga clic en **Agregar** y, a continuación, en Salida de **proyecto**.
2. En el cuadro de diálogo Agregar grupo de salida de **proyecto,** seleccione **ExcelAddIn** en la lista de proyectos y **Salida principal**.
3. Haga clic en **Aceptar** para agregar la salida del proyecto al proyecto de instalación.

    ![Captura de pantalla del cuadro de diálogo Configurar proyecto Agregar grupo de salida de proyecto](media/setup-project-figure-2.png)

    **Figura 2: Configurar proyecto Agregar grupo de salida de proyecto diálogo**

El proyecto de instalación debe implementar el manifiesto de implementación y el manifiesto de aplicación. Agregue estos dos archivos al proyecto de instalación como archivos independientes desde la carpeta de salida del proyecto ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Para agregar los manifiestos de implementación y aplicación

1. En el Explorador de **soluciones**, haga clic con el botón secundario en **OfficeAddInSetup**, haga clic en **Agregar**y, a continuación, en **Archivo**.
2. En el cuadro de diálogo **Agregar archivos,** vaya al directorio de salida **ExcelAddIn.** Normalmente, el directorio de salida es la subcarpeta **bin\\release** del directorio raíz del proyecto, dependiendo de la configuración de compilación seleccionada.
3. Seleccione los archivos **ExcelAddIn.vsto** y **ExcelAddIn.dll.manifest** y haga clic en **Abrir** para agregar estos dos archivos al proyecto de instalación.

    ![Captura de pantalla de los manifiestos de aplicación e implementación en el Explorador de soluciones](media/setup-project-figure-3.jpg)

    **Figura 3: Manifiestos de aplicación e implementación para el complemento en el Explorador de soluciones**

Hacer referencia a ExcelAddIn incluye todos los componentes que ExcelAddIn requiere. Estos componentes deben excluirse e implementarse mediante paquetes de requisitos previos para permitir que se registren correctamente. Además, los Términos de licencia de software deben mostrarse y aceptarse antes de que comience la instalación.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Para excluir las dependencias del proyecto ExcelAddIn

1. En el **Explorador**de soluciones , en el nodo **OfficeAddInSetup** , seleccione todos los elementos de dependencia debajo del elemento **Dependencias detectadas,** excepto **Microsoft .NET Framework** o cualquier ensamblado que termine con ** \*. Utilities.dll**. Los ensamblados de Utilidades están diseñados para implementarse junto con la aplicación.
2. Haga clic con el botón derecho en el grupo y seleccione **Propiedades**.
3. En la ventana **Propiedades,** cambie la propiedad **Excluir** a **True** para excluir los ensamblados dependientes del proyecto de instalación. Asegúrese de no excluir ningún ensamblado de Utilidades.

    ![Captura de pantalla del Explorador de soluciones que muestra las dependencias que se excluirán](media/setup-project-figure-4.jpg)

    **Figura 4: Excluyendo las dependencias**

Puede configurar el paquete de Windows Installer para instalar componentes de requisitos previos agregando un programa de instalación, también conocido como arranque. Este programa de instalación puede instalar los componentes de requisitos previos, un proceso llamado arranque.

Para **ExcelAddIn**, estos requisitos previos deben instalarse antes de que el complemento se pueda ejecutar correctamente:

- La versión de Microsoft .NET Framework a la que se dirige la solución de Office.
- Tiempo de ejecución de Microsoft Visual Studio Tools 2010 para Office.

Para configurar componentes dependientes como requisitos previos

1. En el Explorador de **soluciones**, haga clic con el botón secundario en el proyecto **OfficeAddInSetup** y seleccione **Propiedades**.
2. Aparece el cuadro de diálogo Páginas de propiedades de **OfficeAddInSetup.**
3. Haga clic en el botón **Requisitos previos.**
4. En el cuadro de diálogo Requisitos previos, seleccione la versión correcta de .NET Framework y Microsoft Visual Studio Tools para Office Runtime.

    ![Captura de pantalla del cuadro de diálogo Requisitos previos](media/setup-project-figure-5.png)

    **Figura 5: Cuadro de diálogo Requisitos previos**

    > [!NOTE]
    >Algunos de los paquetes de requisitos previos configurados en el proyecto de instalación de Visual Studio dependen de la configuración de compilación seleccionada. Debe seleccionar los componentes de requisitos previos adecuados para cada configuración de compilación que utilice.

Microsoft Office localiza complementos mediante claves del Registro. Las claves del\_subárbol HKEY CURRENT\_USER se utilizan para registrar el complemento para cada usuario individual. Las claves del\_subárbol HKEY LOCAL\_MACHINE se utilizan para registrar el complemento para todos los usuarios de la máquina. Para obtener más información acerca de las claves del Registro, vea [Entradas del Registro para complementos VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Para configurar el registro

1. En el Explorador de **soluciones**, haga clic con el botón secundario en **OfficeAddInSetup**.
2. Expanda **Ver**.
3. Haga clic en **Registro** para abrir la ventana del editor del registro.
4. En el editor **Registry(OfficeAddInSetup),** expanda **HKEY\_LOCAL\_MACHINE** y, a continuación, **Software**.
5. Elimine ** \[la\]** clave del fabricante que se encuentra en **HKEY\_LOCAL\_MACHINE\\Software**.
6. Expanda **\_HKEY\_CURRENT USER** y, a continuación, **Software**.
7. Elimine ** \[la\] ** clave Del fabricante que se encuentra en **Software HKEY\_\_CURRENT USER\\**.
8. Para agregar claves de registro para la instalación del complemento, haga clic con el botón derecho en la clave **User/Machine Hive,** seleccione **New Key**. Utilice el texto **Software** para el nombre de la nueva clave. Haga clic con el botón derecho en la clave **de software** recién creada y cree una nueva clave con el texto **Microsoft**.
9. Utilice un proceso similar para crear toda la jerarquía de claves necesaria para el registro del complemento:

    **Software de\\Hive\\\\de\\\\Usuario/Máquina\\Microsoft Office Excel Addins SampleCompany.ExcelAddIn**

    El nombre de la empresa se utiliza a menudo como prefijo para el nombre del complemento para proporcionar unicidad.

10. Haga clic con el botón derecho en la clave **SampleCompany.ExcelAddIn,** seleccione **Nuevo**y haga clic en **Valor de cadena**. Utilice el texto **Descripción** para el nombre.
11. Utilice este paso para agregar tres valores más:
    - **FriendlyName** de tipo **String**
    - **LoadBehavior** de tipo **DWORD**
    - **Manifiesto** de tipo **String**

12. Haga clic con el botón derecho en el valor **Descripción** del editor del Registro y haga clic en **Ventana Propiedades**. En la **ventana Propiedades**, escriba Complemento **de demostración** de Excel para la propiedad Valor.
13. Seleccione la clave **FriendlyName** en el editor del Registro. En la **ventana Propiedades**, cambie la propiedad **Valor** a Complemento **de demostración**de Excel .
14. Seleccione la clave **LoadBehavior** en el editor del Registro. En la **ventana Propiedades**, cambie la propiedad **Valor** a **3.** El valor 3 para LoadBehavior indica que el complemento debe cargarse al inicio de la aplicación host. Para obtener más información sobre el comportamiento de carga, vea [Entradas del Registro para complementos de VSTO](registry-entries-for-vsto-add-ins.md).

15. Seleccione la clave **Manifest** en el editor del Registro. En la **ventana Propiedades**, cambie la propiedad **Value** a **file:///[TARGETDIR]ExcelAddIn.vsto-vstolocal**

    ![Captura de pantalla del Editor del Registro](media/setup-project-figure-6.png)

    **Figura 6: Configuración de claves del Registro**

      El tiempo de ejecución de VSTO usa esta clave del Registro para buscar el manifiesto de implementación. La macro [TARGETDIR] se reemplazará por la carpeta en la que está instalado el complemento. La macro incluirá el carácter de seguimiento, por lo que el nombre de archivo del manifiesto de implementación debe ser ExcelAddIn.vsto sin el carácter .
      El postfijo **vstolocal,** indica al tiempo de ejecución de VSTO que el complemento debe cargar desde esta ubicación en lugar de la caché ClickOnce. La eliminación de este postfijo hará que el tiempo de ejecución copie la personalización en la caché ClickOnce.

   >[!WARNING]
   >Debe tener mucho cuidado con el Editor del Registro en Visual Studio. Por ejemplo, si establece accidentalmente DeleteAtUninstall para la clave incorrecta, puede eliminar una parte activa del registro, dejando el equipo del usuario en un estado incoherente, o peor aún, roto.

Las versiones de 64 bits de Office usarán el subárbol del Registro de 64 bits para buscar complementos. Para registrar complementos en el subárbol del Registro de 64 bits, la plataforma de destino del proyecto de instalación debe establecerse en solo 64 bits.

1. Seleccione el proyecto **OfficeAddInSetup** en el explorador de soluciones.
2. Vaya a la ventana **Propiedades** y establezca la propiedad **TargetPlatform** en **x64**.

La instalación de un complemento para las versiones de 32 bits y 64 bits de Office, requerirá que cree dos paquetes MSI independientes. Uno para 32 bits y otro para 64 bits.

  ![Captura de pantalla de la ventana Propiedades que muestra la plataforma de destino para registrar complementos con Office de 64 bits](media/setup-project-figure-7.jpg)

  **Figura 7: Plataforma de destino para registrar complementos con Office de 64 bits**

Si el paquete MSI se utiliza para instalar el complemento o la solución, puede instalarse sin los requisitos previos necesarios instalados. Puede usar las condiciones de inicio en MSI para impedir que el complemento se instale si los requisitos previos no están instalados.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configurar una condición de lanzamiento para detectar el tiempo de ejecución de VSTO

1. En el Explorador de **soluciones**, haga clic con el botón secundario en **OfficeAddInSetup**.
2. Expanda **Ver**.
3. Haga clic en **Condiciones de inicio**.
4. En el editor Condiciones de **inicio (OfficeAddInSetup),** haga clic con el botón secundario **en Requisitos en el equipo**de destino y, a continuación, haga clic en Agregar **condición**de inicio del registro . Esta condición de búsqueda puede buscar en el registro una clave que instale el tiempo de ejecución de VSTO. El valor de la clave está disponible para las distintas partes del instalador a través de una propiedad con nombre. La condición de lanzamiento utiliza la propiedad definida por la condición de búsqueda para comprobar si hay un valor determinado.
5. En el editor Condiciones de **inicio (OfficeAddInSetup),** seleccione la condición de búsqueda **Buscar RegistryEntry1,** haga clic con el botón derecho en la condición y seleccione **Ventana Propiedades**.

6. En la ventana **Propiedades** , establezca estas propiedades:
   1. Establezca el valor de **(Nombre)** **en Buscar VSTO 2010 Runtime**.
   2. Cambie el valor de **Property** a **VSTORUNTIMEREDIST**.
   3. Establezca el valor de **RegKey** en **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4R**
   4. Deje la propiedad **Root** establecida **en vsdrrHKLM**.
   5. Cambie la propiedad **Valor** a **Versión**.

7. En el editor Condiciones de **inicio (OfficeAddInSetup),** seleccione la condición de inicio **Condition1,** haga clic con el botón derecho en la condición y seleccione **Ventana Propiedades**.
8. En la ventana Propiedades, establezca estas propiedades:
   1. Establezca **el (Nombre)** en Verificar la disponibilidad en tiempo de ejecución de **VSTO 2010**.
   2. Cambie el valor de la **condición** a **\>VSTORUNTIMEREDIST á"10.0.30319"**
   3. Deje la propiedad **InstallURL** en blanco.
   4. Establezca el **mensaje** en **Visual Studio 2010 Tools for Office Runtime no está instalado. Ejecute Setup.exe para instalar el complemento**.

        ![Captura de pantalla de la ventana Propiedades para la condición de inicio Verificar disponibilidad en tiempo de ejecución](media/setup-project-figure-8.jpg)

        **Figura 8: Ventana Propiedades para la condición de inicio Verificar disponibilidad en tiempo de ejecución**

 La condición de lanzamiento anterior comprueba explícitamente la presencia del tiempo de ejecución de VSTO cuando lo instala el paquete de arranque.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configurar una condición de lanzamiento para detectar el tiempo de ejecución de VSTO instalado por Office

1. En el editor Condiciones de **inicio (OfficeAddInSetup),** haga clic con el botón secundario en Buscar equipo de **destino**y, a continuación, haga clic en Agregar búsqueda **del registro**.
2. Seleccione la condición de búsqueda **Buscar RegistryEntry1,** haga clic con el botón derecho en la condición y seleccione **Ventana Propiedades**.
3. En la ventana **Propiedades** , establezca estas propiedades:
    1. Establezca el valor de **(Name)** en **Search for Office VSTO Runtime**.
    2. Cambie el valor de **Property** a **OfficeRuntime**.
    3. Establezca el valor de **RegKey** en **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4**.
    4. Deje la propiedad **Root** establecida **en vsdrrHKLM**.
    5. Cambie la propiedad **Valor** a **Versión**.

4. En el editor **Launch Conditions(OfficeAddInSetup),** seleccione la condición de inicio **de disponibilidad De vsTO 2010 Runtime** definida anteriormente, haga clic con el botón derecho en la condición y seleccione Ventana **Propiedades**.

5. Cambie el valor de la propiedad **Condition** a **VSTORUNTIMEREDIST \>?"10.0.30319" O OFFICERUNTIME\>?"10.0.21022"**. Los números de versión pueden ser diferentes para usted dependiendo de las versiones del tiempo de ejecución que requiere el complemento.

    ![Captura de pantalla de las propiedades de Windows para la condición de lanzamiento](media/setup-project-figure-9.jpg)
  
    **Figura 9: Propiedades de Windows para la condición de inicio Verificar disponibilidad en tiempo de ejecución a través de Redist u Office**

Si un complemento tiene como destino .NET Framework 4 o posterior, los tipos dentro de los ensamblados de interoperabilidad primarios (PIA), a los que se hace referencia, se pueden incrustar en el ensamblado VSTO.

Para comprobar si los tipos de interoperabilidad se incrustarán en el complemento realizando los pasos siguientes:

1. Expanda el nodo Referencias en el Explorador de soluciones
2. Seleccione una de las referencias PIA, por ejemplo, **Office**.
3. Para ver las ventanas de propiedades, pulsa f4 o selecciona propiedades en el menú contextual Ensamblajes.
4. Compruebe el valor de la propiedad **Incrustar tipos de interoperabilidad**.

Si el valor se establece en **True**, los tipos se están incrustando y puede saltar a la sección Para compilar el proyecto de [**instalación.**](#to-build-the-setup-project)

Para obtener más información, consulte Equivalencia de tipos y tipos de [interoperabilidad incrustados](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Configurar las condiciones de lanzamiento para detectarlo para los PIA de Office

1. En el editor Condiciones de **inicio (OfficeAddInSetup),** haga clic con el botón secundario **en Requisitos en el equipo**de destino y, a continuación, haga clic en Agregar **condición**de inicio de Windows Installer . Esta condición de inicio busca un PIA de Office buscando el identificador de componente específico.
2. Haga clic con el botón derecho en **Buscar componente1** y haga clic en **Ventana Propiedades** para mostrar las propiedades de la condición de inicio.
3. En la **ventana Propiedades**, establezca estas propiedades:

    1. Cambie el valor de la propiedad **(Name)** a **Search for Office Shared PIA**
    2. Cambie el valor de **ComponentID** a Component Id para el componente de Office que está utilizando. Puede encontrar la lista de Identificadores de componentes en la tabla siguiente, por ejemplo, **.64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4**.
    3. Cambie el valor de la propiedad **Property** a **HASSHAREDPIA**.

4. En el editor **Launch Conditions(OfficeAddInSetup),** haga clic con el botón derecho en **Condition1** y haga clic en **Ventana de propiedades** para mostrar las propiedades de la condición de inicio.

5. Cambiar estas propiedades de **Condición1**:

    1. Cambie el **(Nombre)** para **verificar la disponibilidad**de PIA compartido de Office .
    2. Cambie la **condición** a **HASSHAREDPIA**.
    3. Deje **InstallUrl** en blanco.
    4. Cambie el componente **Mensaje** a **Un componente necesario para interactuar con Excel no está disponible. Ejecute setup.exe**.

    ![Captura de pantalla de la ventana Propiedades para la condición de inicio Verificar PIA compartido de Office](media/setup-project-figure-10.jpg)
  
    **Figura 10: Ventana de propiedades para la condición de inicio Verificar PIA compartido de Office**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>IDs de componentes de los ensamblados de interoperabilidad primarios para Microsoft Office

|Ensamblaje de interoperabilidad primario|Office 2010|Office 2013|Office 2013 (64 bits)|Office 2016|Office 2016 (64 bits)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|•EA7564AC-C67D-4868-BE5C-26E4FC2223FF?|C8A65ABE-3270-4FD7-B854-50C8082C8F39?|•E3BD1151-B9CA-4D45-A77E-51A6E0ED322A|C4ACE6DB-AA99-401F-8BE6-8784BD09F003|C4ACE6DB-AA99-401F-8BE6-8784BD09F003|
|InfoPath|N.o 4153F732-D670-4E44-8AB7-500F2B576BDA|N.o 0F825A16-25B2-4771-A497-FC8AF3B355D8|C5BBD36E-B320-47EF-A512-556B99CB7E41?|-|-|
|Outlook|N.o 1D844339-3DAE-413E-BC13-62D6A52816B2|F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136|N.o 7824A03F-28CC-4371-BC54-93D15EFC1E7F|N.o 7C6D92EF-7B45-46E5-8670-819663220E4E-|N.o 7C6D92EF-7B45-46E5-8670-819663220E4E-|
|PowerPoint|EECBA6B8-3A62-44AD-99EB-8666265466F9|N.o 813139AD-6DAB-4DDD-8C6D-0CA30D073B41|N.o 05758318-BCFD-4288-AD8D-81185841C235|•E0A76492-0FD5-4EC2-8570-AE1BAA61DC88?|•E0A76492-0FD5-4EC2-8570-AE1BAA61DC88?|
|Visio|N.o 3EA123B5-6316-452E-9D51-A489E06E2347|C1713368-12A8-41F1-ACA1-934B01AD6EEB|N.o 2CC0B221-22D2-4C15-A9FB-DE818E51AF75|N.o 2D4540EC-2C88-4C28-AE88-2614B5460648|N.o 2D4540EC-2C88-4C28-AE88-2614B5460648|
|Word|N.o 8B74A499-37F8-4DEA-B5A0-D72FC501CEFA|N.o 9FE736B7-B1EE-410C-8D07-082891C3DAC8|N.o 13C07AF5-B206-4A48-BB5B-B8022333E3CA|N.o DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161|N.o DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161|
|Microsoft Forms 2.0|•B2279272-3FD2-434D-B94E-E4E0F8561AC4?|•B2279272-3FD2-434D-B94E-E4E0F8561AC4?|A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC|-|-|
|Microsoft Graph|N.o 011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E|N.o 52DA4B37-B8EB-4B7F-89C1-824654CE4C70|N.o 24706F33-F0CE-4EB4-BC91-9E935394F510|-|-|
|Etiqueta inteligente|N.o 7102C98C-EF47-4F04-A227-FE33650BF954-|N.o 487A7921-EB3A-4262-BB5B-A5736B732486|N.o 74EFC1F9-747D-4867-B951-EFCF29F51AF7|-|-|
|Oficina compartida|N.o 64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4|N.o 6A174BDB-0049-4D1C-86EF-3114CB0C4C4E|N.o 76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05|N.o 625F5772-C1B3-497E-8ABE-7254EDB00506|N.o 625F5772-C1B3-497E-8ABE-7254EDB00506|
|proyecto|N.o 957A4EC0-E67B-4E86-A383-6AF7270B216A|N.o 1C50E422-24FA-44A9-A120-E88280C8C341|N.o 706D7F44-8231-489D-9B25-3025ADE9F114|N.o 107BCD9A-F1DC-4004-A444-33706FC10058|N.o 107BCD9A-F1DC-4004-A444-33706FC10058|

  ![Captura de pantalla de las condiciones de lanzamiento final](media/setup-project-figure-11.jpg)

  **Figura 11: Condiciones finales de lanzamiento**

Puede refinar aún más las condiciones de inicio para la instalación de ExcelAddIn. Por ejemplo, puede ser útil comprobar si la aplicación de Office de destino real está instalada.

### <a name="to-build-the-setup-project"></a>Para compilar el proyecto de configuración

1. En el Explorador de **soluciones**, haga clic con el botón secundario en el proyecto **OfficeAddInSetup** y haga clic en **Generar**.
2. Con el Explorador de **Windows**, vaya al directorio de salida del proyecto **OfficeAddInSetup** y vaya a la carpeta Release o Debug, dependiendo de la configuración de compilación seleccionada. Copie todos los archivos de la carpeta en una ubicación a la que los usuarios puedan acceder.

Para probar la configuración de ExcelAddIn

1. Vaya a la ubicación en la que copió **OfficeAddInSetup.**
2. Haga doble clic en el archivo setup.exe para instalar el complemento **OfficeAddInSetup.** Acepte los Términos de licencia de software que aparezcan y complete el asistente de instalación para instalar el complemento en el equipo del usuario.

La solución de Excel Office debe instalarse y ejecutarse desde la ubicación especificada durante la instalación.

## <a name="additional-requirements-for-document-level-solutions"></a>Requisitos adicionales para soluciones a nivel de documento

La implementación de soluciones de nivel de documento requiere algunos pasos de configuración diferentes en el proyecto de instalación de Windows Installer.

Esta es una lista de los pasos básicos necesarios para implementar una solución de nivel de documento:

- Cree el proyecto de instalación de Visual Studio.
- Agregue la salida principal de la solución de nivel de documento. La salida principal también incluye el documento de Microsoft Office.
- Agregue los manifiestos de implementación y aplicación como archivos sueltos.
- Excluya los componentes dependientes del paquete del instalador (excepto los ensamblados de utilidades).
- Configure paquetes de requisitos previos.
- Configure las condiciones de lanzamiento.
- Compile el proyecto de instalación y copie los resultados en la ubicación de implementación.
- Implemente la solución de nivel de documento en el equipo del usuario ejecutando la instalación.
- Actualice las propiedades del documento personalizado si es necesario.

### <a name="changing-the-location-of-the-deployed-document"></a>Cambio de la ubicación del documento desplegado

Las propiedades dentro de un documento de Office se usan para buscar soluciones de nivel de documento. Si el documento está instalado en la misma carpeta que el ensamblado VSTO, no se requieren cambios. Sin embargo, si se instala en una carpeta diferente, estas propiedades deberán actualizarse durante la instalación.

Para obtener más información acerca de estas propiedades de documento, vea Información general sobre propiedades de [documento personalizadas](custom-document-properties-overview.md).

Para cambiar estas propiedades, debe usar una acción personalizada durante la configuración.

En el ejemplo siguiente se utiliza una solución de nivel de documento denominada ExcelWorkbookProject y un proyecto de instalación denominado ExcelWorkbookSetup. El proyecto ExcelWorkbookSetup se configura mediante los mismos pasos descritos anteriormente, excepto para establecer las claves del Registro.

Para agregar el proyecto de acción personalizado a la solución de Visual Studio

1. Agregue un nuevo proyecto de consola de .NET a la solución haciendo clic con el botón derecho en el proyecto de implementación de **documentos** de Office en el Explorador de **soluciones**
2. Expanda **Agregar** y haga clic en **Nuevo proyecto**.
3. Seleccione la plantilla Aplicación de consola y asigne al proyecto el nombre **AddCustomizationCustomAction**.

    ![Captura de pantalla del Explorador de soluciones - AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figura 12: Explorador de soluciones - AddCustomizationCustomAction**

4. Agregue una referencia a estos ensamblados:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft.VisualStudio.Tools.Applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Copie este código en Program.cs o Program.vb

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

Para agregar la personalización al documento, debe tener el identificador de solución de la solución de nivel de documento de VSTO. Este valor se recupera del archivo de proyecto de Visual Studio.

Para recuperar el identificador de la solución

1. En el menú **Compilar,** haga clic en **Compilar solución** para compilar la solución de nivel de documento y agregar la propiedad de identificador de solución al archivo de proyecto.
2. En el Explorador de **soluciones**, haga clic con el botón secundario en el proyecto de nivel de documento **ExcelWorkbookProject**
3. Haga clic en **UnloadProject** para tener acceso al archivo de proyecto desde Dentro de Visual Studio.

    ![Captura de pantalla de la solución de descarga de documentos de Excel del Explorador de soluciones](media/setup-project-figure-16.jpg)

    **Figura 13: Descarga de la solución de documentos de Excel**

4. En el **Explorador**de soluciones , haga clic con el botón secundario en **ExcelWorkbookProject** y haga clic en **EditExcelWorkbookProject.vbproj** o **Editar ExcelWorkbookProject.csproj**.
5. En el **ExcelWorkbookProject** editor, busque el **SolutionID** elemento dentro de la **PropertyGroup** elemento.
6. Copie el valor GUID de este elemento.

    ![Recuperar el SolutionID](media/setup-project-figure-17.jpg)

    **Figura 14: Recuperación del SolutionID**

7. En el **Explorador**de soluciones , haga clic con el botón secundario en **ExcelWorkbookProject** y haga clic en **Volver a cargar proyecto**.
8. Haga clic en **Sí** en el cuadro de diálogo que aparece para cerrar el editor **ExcelWorkbookProject.**
9. El identificador de **solución** se usará en la acción instalar personalizada.

El último paso es configurar la acción personalizada para los pasos **Instalar** y **Desinstalar.**

### <a name="to-configure-the-setup-project"></a>Para configurar el proyecto de configuración

1. En el **Explorador**de soluciones , haga clic con el botón secundario en **ExcelWorkbookSetup**, expanda **Agregar** y haga clic en **Salida de proyecto**.
2. En el cuadro de diálogo **Agregar grupo** de salida de proyecto , en la lista **Proyecto** , haga clic en **AddCustomizationCustomAction**.
3. Seleccione **Salida principal** y haga clic en **Aceptar** para cerrar el cuadro de diálogo y agregar el ensamblado que contiene la acción personalizada al proyecto de instalación.

    ![Captura de pantalla de la ventana Acción personalizada del manifiesto del documento - Agregar grupo de salida del proyecto](media/setup-project-figure-18.jpg)

    **Figura 15: Acción personalizada del manifiesto del documento - Agregar grupo de salida del proyecto**

4. En el Explorador de **soluciones**, haga clic con el botón secundario en **ExcelWorkbookSetup**.
5. Expanda **Ver** y haga clic en **Acciones personalizadas**.
6. En el editor **Acciones personalizadas(ExcelWorkbookSetup),** haga clic con el botón derecho en **Acciones personalizadas** y haga clic en **Agregar acción personalizada**.
7. En el cuadro de diálogo **Seleccionar elemento en proyecto,** en la lista **Buscar** en , haga clic en **Carpeta de**aplicación . Seleccione **Salida principal en AddCustomizationCustomAction(active)** y haga clic en **Aceptar** para agregar la acción personalizada al paso Instalar.
8. En el **nodo Instalar**, haga clic con el botón derecho en Salida principal **de AddCustomizationCustomAction(Active)** y haga clic en **Cambiar nombre**. Asigne al **documento Copiar documento personalizado el nombre Mis documentos y adjunte**la personalización .
9. En el **nodo Desinstalar**, haga clic con el botón derecho en Salida principal **de AddCustomizationCustomAction(Active)** y haga clic en **Cambiar nombre**. Asigne un nombre a la acción personalizada **Quitar documento de la carpeta Documentos**.

    ![Captura de pantalla de la ventana Acciones personalizadas del manifiesto del documento](media/setup-project-figure-19.jpg)

    **Figura 16: Acciones personalizadas del manifiesto del documento**

10. En el editor **Acciones personalizadas(ExcelWorkbookSetup),** haga clic con el botón derecho en **Copiar documento en Mis documentos y adjunte** la personalización y haga clic en **Ventana Propiedades**.
11. En la ventana **Propiedades** **de CustomActionData,** escriba la ubicación del archivo DLL de personalización, el manifiesto de implementación y la ubicación del documento de Microsoft Office. El SolutionID también es necesario.
12. Si desea registrar cualquier error de configuración en un archivo, incluya un parámetro LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Captura de pantalla de la acción personalizada para copiar documento en la ventana Propiedades de mis documentos](media/setup-project-figure-20.jpg)

    **Figura 17: Acción personalizada para copiar documentos en mis documentos**

13. La acción personalizada para desinstalar necesita el nombre del documento, puede proporcionar que mediante el mismo documentLocation parámetro en el **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compile e implemente el proyecto **ExcelWorkbookSetup.**
15. Busque en la carpeta **Mis documentos** y abra el archivo ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Recursos adicionales

[Cómo: Instalar Visual Studio Tools para Office Runtime](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Ensamblados de interoperabilidad primarios de Office](office-primary-interop-assemblies.md)

[Entradas de registro para complementos VSTO](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Especificación de regiones de formulario en el Registro de Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Granting Trust to Documents](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Acerca de los autores

Wouter van Vugt es un MVP de Microsoft con tecnologías Office Open XML y un consultor independiente que se centra en la creación de aplicaciones empresariales de Office (OBA) con SharePoint, Microsoft Office y tecnologías .NET relacionadas.
Wouter es un colaborador frecuente de sitios de la comunidad de desarrolladores como [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Ha publicado varios artículos y artículos, así como un libro disponible en línea titulado Open XML: Explained e-book.
Wouter es el fundador de Code-Counsel, una empresa holandesa que se centra en la entrega de contenido técnico de vanguardia a través de una variedad de canales. Puede obtener más información sobre Wouter leyendo su blog.

Ted Pattison es MVP de SharePoint, autor, formador y fundador de Ted Pattison Group. En el otoño de 2005, Ted fue contratado por el grupo evangelismo de plataforma de desarrolladores de Microsoft para crear el plan de estudios de formación de desarrolladores de Ascend para Windows SharePoint Services 3.0 y Microsoft Office SharePoint Server 2007. Desde entonces, Ted se ha centrado por completo en la educación de desarrolladores profesionales sobre tecnologías de SharePoint 2007. Ted ha terminado de escribir un libro para Microsoft Press titulado Inside Windows SharePoint Services 3.0 que se centra en cómo usar SharePoint como una plataforma de desarrollo para crear soluciones empresariales. Ted también escribe una columna centrada en el desarrollador para MSDN Magazine titulada Office Space.
