---
title: Implementar una solución de Office mediante ClickOnce
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b725e7bc198396a7070bdfa869471950a863f3dc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674066"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Implementar una solución de Office mediante ClickOnce
  Puede implementar su solución de Office en menos pasos si usa ClickOnce. Si publica actualizaciones, la solución las detectará e instalará automáticamente. Sin embargo, ClickOnce requiere que instale la solución por separado para cada usuario de un equipo. Por lo tanto, debe considerar el uso de Windows Installer (*.msi*) si más de un usuario ejecutará la solución en el mismo equipo.  
  
## <a name="in-this-topic"></a>En este tema  
  
-   [Publicar la solución](#Publish)  
  
-   [Decidir cómo conceder confianza a la solución](#Trust)  
  
-   [Ayudar a los usuarios a instalar la solución](#Helping)  
  
-   [Colocar el documento de una solución en el equipo del usuario final (solo para personalizaciones de nivel de documento)](#Put)  
  
-   [Colocar el documento de una solución en un servidor que ejecute SharePoint (solo para personalizaciones de nivel de documento)](#SharePoint)  
  
-   [Crear a un instalador personalizado](#Custom)  
  
-   [Publicar una actualización](#Update)  
  
-   [Cambiar la ubicación de instalación de una solución](#Location)  
  
-   [Revertir una solución a una versión anterior](#Roll)  
  
 Para obtener más información sobre cómo implementar una solución de Office mediante la creación de un archivo de Windows Installer, consulte [implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Publish"></a> Publicar la solución  
 Puede publicar la solución mediante el **Asistente para publicación** o **Diseñador de proyectos**. En este procedimiento, usará el **Diseñador de proyectos** porque proporciona el conjunto completo de opciones de publicación. Consulte [Asistente para publicación &#40;desarrollo de Office en Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).  
  
#### <a name="to-publish-the-solution"></a>Para publicar la solución  
  
1.  En **el Explorador de soluciones**, elija el nodo que se denomina para el proyecto.  
  
2.  En la barra de menús, elija **proyecto**, *ProjectName* **propiedades**.  
  
3.  En el **Diseñador de proyectos**, elija el **publicar** ficha, que se muestra en la siguiente ilustración.  
  
     ![La pestaña publicar del Diseñador de proyectos](../vsto/media/vsto-publishtab.png "la ficha Publicar del Diseñador de proyectos")  
  
4.  En el **ubicación de la carpeta de publicación (servidor ftp o ruta de acceso de archivo)** , escriba la ruta de acceso de la carpeta donde desea que el **Diseñador de proyectos** para copiar los archivos de solución.  
  
     Puede especificar cualquiera de los siguientes tipos de rutas.  
  
    -   Una ruta de acceso local (por ejemplo, *C:\FolderName\FolderName*).  
  
    -   Una ruta de acceso de convención de nomenclatura universal (UNC) a una carpeta en la red (por ejemplo,  *\\\ServerName\FolderName*).  
  
    -   Una ruta de acceso relativa (por ejemplo, *carpetaDePublicación\\*, que es la carpeta en la que se publica el proyecto de forma predeterminada).  
  
5.  En el **dirección URL de la carpeta de instalación** , escriba la ruta de acceso completa de la ubicación donde los usuarios finales encontrarán su solución.  
  
     Si aún no conoce la ubicación, no especifique nada en este campo. De forma predeterminada, ClickOnce busca actualizaciones en la carpeta en la que los usuarios instalan la solución.  
  
6.  Elija el botón **Requisitos previos** .  
  
7.  En el **requisitos previos** diálogo cuadro, asegúrese de que el **crear programa de instalación para instalar los componentes necesarios** casilla está activada.  
  
8.  En el **elegir qué requisitos previos para instalar** lista, seleccione las casillas de verificación para **Windows Installer 4.5** y el paquete de .NET Framework adecuado.  
  
     Por ejemplo, si su solución tiene como destino el [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], active las casillas de verificación de **Windows Installer 4.5** y **Microsoft .NET Framework 4.5 Full**.  
  
9. Si su solución tiene como destino .NET Framework 4.5, seleccione también el **Visual Studio 2010 Tools para Office Runtime** casilla de verificación.  
  
    > [!NOTE]  
    >  De forma predeterminada, esta casilla no aparece. Para mostrar esta casilla, debe crear un paquete de programa previo. Consulte [crear un paquete de programa previo para un Office 2013 complemento VSTO con Visual Studio 2012](http://blogs.msdn.com/b/vsto/archive/2012/12/21/creating-a-bootstrapper-package-for-an-office-2013-vsto-add-in-with-visual-studio-2012.aspx).  
  
10. En **especificar la ubicación de instalación de requisitos previos**, elija una de las opciones que aparecen y, a continuación, elijan el **Aceptar** botón.  
  
     En la siguiente tabla se describe cada una de las opciones.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |**Descargar los requisitos previos del sitio web del proveedor de los componentes**|Se pedirá al usuario que descargue e instale estos requisitos previos del proveedor.|  
    |**Descargar los requisitos previos de la misma ubicación que mi aplicación**|El software necesario se instala con la solución. Si elige esta opción, Visual Studio copia automáticamente todos los paquetes de requisitos previos en la ubicación de publicación. Para que esta opción funcione, los paquetes se deben encontrar en el equipo de desarrollo.|  
    |**Descargar los requisitos previos de la siguiente ubicación**|Visual Studio copia todos los paquetes de requisitos previos en la ubicación especificada y los instala con la solución.|  
  
     Consulte [cuadro de diálogo de requisitos previos](/visualstudio/ide/reference/prerequisites-dialog-box).  
  
11. Elija la **actualizaciones** botón, especifique con qué frecuencia desea que cada usuario final complementos de VSTO o personalización para comprobar si hay actualizaciones y, a continuación, elija el **Aceptar** botón.  
  
    > [!NOTE]  
    >  Si va a implementar mediante un CD o una unidad extraíble, elija el **buscar nunca actualizaciones** botón de opción.  
  
     Para obtener información sobre cómo publicar una actualización, vea [publicar una actualización](#Update).  
  
12. Elija la **opciones** botón, revise las opciones en el **opciones** diálogo cuadro y, a continuación, elija el **Aceptar** botón.  
  
13. Elija la **publicar ahora** botón.  
  
     Visual Studio agrega las siguientes carpetas y archivos a la carpeta de publicación especificada anteriormente en este procedimiento.  
  
    -   El **archivos de la aplicación** carpeta.  
  
    -   El programa de instalación  
  
    -   Un manifiesto de implementación que apunta al manifiesto de implementación de la última versión  
  
     El **archivos de la aplicación** carpeta contiene una subcarpeta para cada versión que se publica. Cada subcarpeta específica de la versión contiene los archivos siguientes.  
  
    -   Un manifiesto de aplicación  
  
    -   Un manifiesto de implementación  
  
    -   Ensamblados de personalización  
  
     En la siguiente ilustración se muestra la estructura de la carpeta de publicación de un complemento de VSTO de Outlook.  
  
     ![Publicar la estructura de carpetas](../vsto/media/publishfolderstructure.png "publicar la estructura de carpetas")  
  
    > [!NOTE]  
    >  ClickOnce anexa la *.deploy* extensión a los ensamblados para que una instalación segura de Internet Information Services (IIS) no bloquee los archivos debido a una extensión no segura. Cuando el usuario instala la solución, ClickOnce quitará la *.deploy* extensión.  
  
14. Copie los archivos de la solución en la ubicación de instalación especificada anteriormente en este procedimiento.  
  
##  <a name="Trust"></a> Decidir cómo conceder confianza a la solución  
 Para que una solución pueda ejecutarse en los equipos de los usuarios, debe conceder confianza o los usuarios deben responder al mensaje relativo a la confianza cuando instalen la solución. Para conceder confianza a la solución, firme los manifiestos mediante un certificado que identifique un publicador de confianza conocido. Consulte [confiar en la solución de firmar los manifiestos de aplicación e implementación](../vsto/granting-trust-to-office-solutions.md#Signing).  
  
 Si va a implementar una personalización de nivel de documento y desea colocar el documento en una carpeta en el equipo del usuario o que el documento esté disponible en un sitio de SharePoint, asegúrese de que Office confíe en la ubicación del documento. Consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
##  <a name="Helping"></a> Ayudar a los usuarios a instalar la solución  
 Los usuarios pueden instalar la solución ejecutando el programa de instalación, abriendo el manifiesto de implementación o, en el caso de una personalización de nivel de documento, abriendo el documento directamente. El procedimiento recomendado es que los usuarios instalen la solución mediante el programa de instalación. Los otros dos enfoques no garantizan que el software necesario está instalado. Si los usuarios desean abrir el documento desde la ubicación de instalación, deben agregarlo a la lista de ubicaciones de confianza en el Centro de confianza de la aplicación de Office.  
  
### <a name="opening-the-document-of-a-document-level-customization"></a>Abrir el documento de una personalización de nivel de documento  
 Los usuarios pueden abrir el documento de una personalización de nivel de documento directamente desde la ubicación de instalación o copiando el documento en el equipo local y después abriendo la copia.  
  
 Como procedimiento recomendado, los usuarios deben abrir una copia del documento en sus equipos para impedir que varios usuarios intenten abrir la misma copia al mismo tiempo. Para aplicar esta práctica recomendada, puede configurar el programa de instalación de forma que copie el documento en los equipos de los usuarios. Consulte [colocar el documento de una solución en el equipo del usuario final (solo para personalizaciones de nivel de documento)](#Put).  
  
### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Instalar la solución abriendo el manifiesto de implementación desde un sitio Web de IIS  
 Los usuarios pueden instalar una solución de Office abriendo el manifiesto de implementación desde la Web. Sin embargo, una instalación segura de Internet Information Services (IIS) bloqueará los archivos que tienen la *.vsto* extensión. El tipo MIME se debe definir en IIS para poder implementar una solución de Office mediante IIS.  
  
##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Para agregar el tipo MIME .vsto a IIS 6.0  
  
1.  En el servidor que ejecuta IIS 6.0, elija **iniciar** > **todos los programas** > **herramientas administrativas**  >   **De Internet Information Services (IIS) Manager**. 
  
2.  Elija el nombre del equipo, el **sitios Web** carpeta o el sitio web que está configurando.  
  
3.  En la barra de menús, elija **acción** > **propiedades**.  
  
4.  En el **encabezados HTTP** ficha, elija la **tipos MIME** botón.  
  
5.  En el **tipos MIME** ventana, elija el **New** botón.  
  
6.  En el **tipo MIME** ventana, escriba **.vsto** como la extensión, escriba **application/x-ms-vsto** como MIME escriba y, a continuación, aplicar la nueva configuración.  
  
    > [!NOTE]  
    >  Para que los cambios surtan efecto, debe reiniciar el Servicio de publicación World Wide Web o esperar hasta que el proceso de trabajo se recicle. Debe Vaciar caché de disco del explorador y, a continuación, intente abrir el *.vsto* archivo nuevo.  
  
##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Para agregar el tipo MIME .vsto a IIS 7,0  
  
1.  En el servidor que ejecuta IIS 7.0, elija **iniciar** > **todos los programas** > **Accesorios**.  
  
2.  Abra el menú contextual para **símbolo**y, a continuación, elija **ejecutar como administrador.**  
  
3.  En el **abierto** cuadro, escriba la siguiente ruta de acceso y, a continuación, elija el **Aceptar** botón.  
  
    ```cmd
    %windir%\system32\inetsrv   
    ```  
  
4.  Escriba el comando siguiente y, a continuación, aplique la nueva configuración.  
  
    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  
  
    > [!NOTE]  
    >  Para que los cambios surtan efecto, debe reiniciar el Servicio de publicación World Wide Web o debe esperar hasta que el proceso de trabajo se recicle. Debe Vaciar caché de disco del explorador y, a continuación, intente abrir el *.vsto* archivo nuevo.  
  
##  <a name="Put"></a> Colocar el documento de una solución en el equipo del usuario final (solo para personalizaciones de nivel de documento)  
 Puede copiar el documento de la solución en el equipo del usuario final para ellos mediante la creación de una acción posterior a la implementación. De este modo, el usuario no tiene que copiar manualmente el documento desde la ubicación de instalación en su equipo después de instalar la solución. Tendrá que crear una clase que define la acción posterior a la implementación, compilar y publicar la solución, modificar el manifiesto de aplicación y volver a firmar el manifiesto de aplicación e implementación.  
  
 Los procedimientos siguientes se supone que es el nombre del proyecto **ExcelWorkbook** y que publique la solución en el **C:\publish** directorio en el equipo.  
  
### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Crear una clase que defina la acción posterior a la implementación  
  
1.  En la barra de menús, elija **archivo** > **agregar** > **nuevo proyecto**.  
  
2.  En el **Agregar nuevo proyecto** cuadro de diálogo el **plantillas instaladas** panel, elija el **Windows** carpeta.  
  
3.  En el **plantillas** panel, elija el **biblioteca de clases** plantilla.  
  
4.  En el **nombre** , introduzca **FileCopyPDA**y, a continuación, elija el **Aceptar** botón.  
  
5.  En **el Explorador de soluciones**, elija el **FileCopyPDA** proyecto.  
  
6.  En la barra de menús, elija **proyecto** > **Agregar referencia**.  
  
7.  En el **.NET** pestaña, agregue referencias a `Microsoft.VisualStudio.Tools.Applications.Runtime` y `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.  
  
8.  Cambie el nombre de la clase a `FileCopyPDA` y reemplace el contenido del archivo con el código. Este código realiza las tareas siguientes:  
  
    -   Copia el documento en el escritorio del usuario.  
  
    -   Cambia la propiedad _AssemblyLocation desde una ruta de acceso relativa a una ruta de acceso completa para el manifiesto de implementación.  
  
    -   Elimina el archivo si el usuario desinstala la solución.  
  
     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]  
  
### <a name="build-and-publish-the-solution"></a>Compilar y publicar la solución  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **FileCopyPDA** del proyecto y, a continuación, elija **compilar**.  
  
2.  Abra el menú contextual para el **ExcelWorkbook** del proyecto y, a continuación, elija **compilar**.  
  
3.  Abra el menú contextual para el **ExcelWorkbook** del proyecto y, a continuación, elija **Agregar referencia**.  
  
4.  En el **Agregar referencia** diálogo cuadro, elija el **proyectos** ficha, elija **FileCopyPDA**y, a continuación, elija el **Aceptar** botón.  
  
5.  En **el Explorador de soluciones**, elija el **ExcelWorkbook** proyecto.  
  
6.  En la barra de menús, elija **proyecto** > **nueva carpeta**.  
  
7.  ENTRAR **datos**y, a continuación, elija el **ENTRAR** clave.  
  
8.  En **el Explorador de soluciones**, elija el **datos** carpeta.  
  
9. En la barra de menús, elija **proyecto** > **Agregar elemento existente**.  
  
10. En el **Agregar elemento existente** cuadro de diálogo, vaya al directorio de salida para el **ExcelWorkbook** del proyecto, elija el **ExcelWorkbook.xlsx** de archivo y, a continuación, elija el  **Agregar** botón.  
  
11. En **el Explorador de soluciones** elegir el **ExcelWorkbook.xlsx** archivo.  
  
12. En el **propiedades** ventana, cambie el **acción de compilación** propiedad **contenido** y el **Copy to Output Directory** propiedad  **Copiar si es posterior**.  
  
     Cuando haya completado estos pasos, el proyecto será similar a la siguiente ilustración.  
  
     ![Estructura del proyecto de la acción posterior a la implementación. ](../vsto/media/vsto-postdeployment.png "Estructura de proyecto de la acción posterior a la implementación.")  
  
13. Publicar el **ExcelWorkbook** proyecto.  
  
### <a name="modify-the-application-manifest"></a>Modificar el manifiesto de aplicación  
  
1.  Abra el **c:\publish** directorio mediante el uso de **Explorador de archivos**.  
  
2.  Abra el **archivos de la aplicación** carpeta y, a continuación, abra la carpeta que corresponde a la más reciente publican la versión de la solución.  
  
3.  Abra el **ExcelWorkbook.dll.manifest** archivo en un editor de texto como Bloc de notas.  
  
4.  Agregue el código siguiente detrás del elemento `</vstav3:update>`. El atributo de clase de la `<vstav3:entryPoint>` elemento, use la siguiente sintaxis: *NamespaceName.ClassName*. En el ejemplo siguiente, los nombres de clase y espacio de nombres son los mismos, por lo que el nombre del punto de entrada resultante es `FileCopyPDA.FileCopyPDA`.  
  
    ```xml
    <vstav3:postActions>  
      <vstav3:postAction>  
        <vstav3:entryPoint  
          class="FileCopyPDA.FileCopyPDA">  
          <assemblyIdentity  
            name="FileCopyPDA"  
            version="1.0.0.0"  
            language="neutral"  
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
        <vstav3:postActionData>  
        </vstav3:postActionData>  
      </vstav3:postAction>  
    </vstav3:postActions>  
    ```  
  
### <a name="re-sign-the-application-and-deployment-manifests"></a>Volver a firmar los manifiestos de aplicación e implementación  
  
1.  En el **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** carpeta, copie el **ExcelWorkbook_TemporaryKey.pfx** archivo de certificado y, a continuación, péguelo en el  *CarpetaDePublicación* **\Application Files\ExcelWorkbook**\__Versiónpublicadamásreciente_ carpeta.
  
2.  Abra el símbolo del sistema de Visual Studio y, a continuación, cambie los directorios a la **c:\publish\Application de aplicación\excelworkbook**\__Versiónpublicadamásreciente_ carpeta (por ejemplo, **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).  
  
3.  Firme el manifiesto de aplicación modificado ejecutando el siguiente comando:  
  
    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  
  
     Aparece el mensaje "ExcelWorkbook.dll.manifest firmado correctamente".  
  
4.  Cambie a la **c:\publish** manifiesto carpeta y, a continuación, actualización y la implementación del inicio de sesión, ejecute el comando siguiente:  
  
    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  
  
    > [!NOTE]  
    >  En el ejemplo anterior, reemplace MostRecentVersionNumber con el número de versión de la versión publicada más recientemente de la solución (por ejemplo, **1_0_0_4**).  
  
     Aparece el mensaje "ExcelWorkbook.vsto firmado correctamente".  
  
5.  Copia el *ExcelWorkbook.vsto* del archivo a la **c:\publish\Application de aplicación\excelworkbook**\__MostRecentVersionNumber_ directory.  
  
##  <a name="SharePoint"></a> Colocar el documento de una solución en un servidor que ejecute SharePoint (solo para personalizaciones de nivel de documento)  
 Puede publicar la personalización de nivel de documento para los usuarios finales mediante SharePoint. Cuando los usuarios van al sitio de SharePoint y abren el documento, el runtime instala automáticamente la solución desde la carpeta de red compartida en el equipo local del usuario. Una vez instalada localmente la solución, la personalización seguirá funcionando aunque el documento se copie en otra parte, como el escritorio.  
  
#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Para colocar el documento en un servidor que ejecuta SharePoint  
  
1.  Agregue el documento de la solución a una biblioteca de documentos en un sitio de SharePoint.  
  
2.  Siga los pasos de alguno de estos enfoques:  
  
    -   Utilice la herramienta de configuración de Office para agregar el servidor que ejecuta SharePoint al Centro de confianza de Word o Excel en todos los equipos de los usuarios.  
  
         Consulte [las directivas de seguridad y configuración de Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).  
  
    -   Asegúrese de que cada usuario realice los pasos siguientes.  
  
        1.  En el equipo local, abra Word o Excel, elija el **archivo** pestaña y, a continuación, elija el **opciones** botón.  
  
        2.  En el **centro de confianza** diálogo cuadro, elija el **ubicaciones de confianza** botón.  
  
        3.  Seleccione el **Permitir ubicaciones de confianza en la red (no recomendado)** casilla de verificación y, a continuación, elija el **agregar nueva ubicación** botón.  
  
        4.  En el **ruta** , escriba la dirección URL de la biblioteca de documentos de SharePoint que contiene el documento cargado (por ejemplo, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).  
  
             No agregue el nombre de la página Web predeterminada, como *default.aspx* o *AllItems.aspx*.  
  
        5.  Seleccione el **las subcarpetas de esta ubicación también son de confianza** casilla de verificación y, a continuación, elija el **Aceptar** botón.  
  
             Cuando los usuarios abran el documento desde el sitio de SharePoint, se abrirá el documento y se instalará la personalización. Los usuarios pueden copiar el documento en el escritorio. La personalización se ejecutará igualmente porque las propiedades del documento apuntan a la ubicación de red del documento.  
  
##  <a name="Custom"></a> Crear a un instalador personalizado  
 Puede crear a un instalador personalizado para la solución de Office, en lugar de usar el programa de instalación que se crea automáticamente al publicar la solución. Por ejemplo, podría usar un script de inicio de sesión para iniciar la instalación o podría usar un archivo por lotes para instalar la solución sin interacción del usuario. Estos escenarios funcionan mejor si los requisitos previos ya están instalados en los equipos de los usuarios finales.  
  
 Como parte del proceso de instalación personalizada, llame a la herramienta de instalación para las soluciones de Office (*VSTOInstaller.exe*), que se instala en la siguiente ubicación predeterminada:  
  
 *%CommonProgramFiles%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*  
  
 Si la herramienta no se encuentra en esa ubicación, puede usar el **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** o **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4 \InstallerPath** clave del registro para buscar la ruta de acceso a esa herramienta.  
  
 Puede usar los siguientes parámetros con *VSTOinstaller.exe*.  
  
|Parámetro|Definición|  
|---------------|----------------|  
|/Install o /I|Instala la solución. Esta opción debe ir seguida de la ruta de acceso de un manifiesto de implementación. Puede especificar una ruta de acceso en el equipo local —un recurso compartido de archivos de convención de nomenclatura universal (UNC)—. Puede especificar una ruta de acceso local (*C:\FolderName\PublishFolder*), una ruta de acceso relativa (*publicar\\*), o una ubicación completa (*\\\ServerName\ NombreDeCarpeta* o http://*nombreDeServidor/nombreDeCarpeta*).|  
|/Uninstall o /U|Desinstala la solución. Esta opción debe ir seguida de la ruta de acceso de un manifiesto de implementación. Puede especificar que una ruta de acceso puede estar en el equipo local, en un recurso compartido de archivos UNC. Puede especificar una ruta de acceso local (*c:\FolderName\PublishFolder*), una ruta de acceso relativa (*publicar\\*), o una ubicación completa (*\\\ServerName\ NombreDeCarpeta* o http://*nombreDeServidor/nombreDeCarpeta*).|  
|/Silent o /S|Instala o desinstala sin solicitar la entrada de datos del usuario ni mostrar ningún mensaje. Si se requiere un símbolo del sistema de confianza, la personalización no está instalada o actualizada.|  
|/Help o /?|Muestra la información de Ayuda.|  
  
 Al ejecutar *VSTOinstaller.exe*, es posible que aparezcan los siguientes códigos de error.  
  
|Código de error|Definición|  
|----------------|----------------|  
|0|La solución se instaló o desinstaló correctamente o se mostró la Ayuda de VSTOInstaller.|  
|-100|Una o más opciones de la línea de comandos no son válidas o se establecieron más de una vez. Para obtener más información, escriba "¿vstoinstaller /?" o bien consulte [crear un instalador personalizado para una solución de ClickOnce Office](http://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|  
|-101|Una o varias opciones de línea de comandos no es válido. Para obtener más información, escriba “vstoinstaller/?”.|  
|-200|El URI del manifiesto de implementación no es válido. Para obtener más información, escriba “vstoinstaller/?”.|  
|-201|No se pudo instalar la solución porque el manifiesto de implementación no es válido. Consulte [manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md).|  
|-202|No se pudo instalar la solución porque Visual Studio Tools para la sección de Office del manifiesto de aplicación no es válido. Consulte [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).|  
|-203|No se pudo instalar la solución porque se produjo un error en la descarga. Compruebe el URI o la ubicación del archivo de red del manifiesto de implementación e inténtelo de nuevo.|  
|-300|No se pudo instalar la solución porque se produjo una excepción de seguridad. Consulte [soluciones de Office Secure](../vsto/securing-office-solutions.md).|  
|-400|No se pudo instalar la solución.|  
|-401|No se pudo desinstalar la solución.|  
|-500|Se ha cancelado la operación porque no se pudo instalar o desinstalar la solución o porque no se pudo descargar el manifiesto de implementación.|  
  
##  <a name="Update"></a> Publicar una actualización  
 Para actualizar una solución, publíquela de nuevo mediante el uso de la **Diseñador de proyectos** o **Asistente para publicación**, y, a continuación, copie la solución actualizada en la ubicación de instalación. Cuando copie los archivos en la ubicación de instalación, asegúrese de sobrescribir los archivos anteriores.  
  
 La próxima vez que comprueba la solución para una actualización, lo encontrará y cargar la nueva versión automáticamente.  
  
##  <a name="Location"></a> Cambiar la ubicación de instalación de una solución  
 Puede agregar o cambiar la ruta de instalación después de publicar una solución. Puede cambiar la ruta de instalación por alguna de las siguientes razones:  
  
-   El programa de instalación se compiló antes de que se conociera la ruta de instalación.  
  
-   Los archivos de la solución se han copiado en otra ubicación.  
  
-   El servidor que hospeda los archivos de instalación tiene un nombre o una ubicación nuevos.  
  
 Para cambiar la ruta de instalación de una solución, debe actualizar el programa de instalación. Los usuarios tendrán que ejecutar este programa. Para las personalizaciones de nivel de documento, los usuarios también deben actualizar una propiedad en el documento para que apunte a la nueva ubicación.  
  
> [!NOTE]  
>  Si no desea pedir a los usuarios para actualizar las propiedades del documento, puede pedir a los usuarios obtener el documento actualizado de la ubicación de instalación.  
  
#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Para cambiar la ruta de instalación en el programa de instalación  
  
1.  Abra un **símbolo** ventana y, a continuación, cambie los directorios a la carpeta de instalación.  
  
2.  Ejecute el programa de instalación e incluya el parámetro `/url`, que toma la nueva ruta de instalación como una cadena.  
  
     En el ejemplo siguiente se muestra cómo cambiar la ruta de instalación a una ubicación del sitio web de Fabrikam, pero puede reemplazar esa dirección URL por la ruta que desee:  
  
    ```cmd  
    setup.exe /url="http://www.fabrikam.com/newlocation"  
    ```  
  
    > [!NOTE]  
    >  Si aparece un mensaje y se indica que la firma del archivo ejecutable se va a invalidar, el certificado utilizado para firmar la solución ya no es válido y se desconoce el publicador. Como resultado, los usuarios deberán confirmar que confían en el origen de la solución para poder instalarla.  
  
    > [!NOTE]  
    >  Para mostrar el valor actual de la dirección URL, ejecute `setup.exe /url`.  
  
 Para las personalizaciones de nivel de documento, los usuarios deben abrir el documento y, a continuación, actualice su propiedad _AssemblyLocation. Los pasos siguientes describen cómo los usuarios pueden realizar esta tarea.  
  
#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>Para actualizar la propiedad _AssemblyLocation en un documento  
  
1.  En el **archivo** ficha, elija **información**, que se muestra en la siguiente ilustración.  
  
     ![Pestaña información de Excel](../vsto/media/vsto-infotab.png "pestaña información de Excel")  
  
2.  En el **propiedades** elija **propiedades avanzadas**, que se muestra en la siguiente ilustración.  
  
     ![Propiedades avanzadas de Excel. ](../vsto/media/vsto-advanceddocumentproperties.png "Propiedades avanzadas en Excel.")  
  
3.  En el **personalizado** pestaña en el **propiedades** elija _AssemblyLocation, como se muestra en la ilustración siguiente.  
  
     ![La propiedad AssemblyLocation. ](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation la propiedad.")  
  
     El **valor** cuadro contiene el identificador del manifiesto de implementación.  
  
4.  Delante del identificador, escriba la ruta de acceso completa del documento, seguido por una barra, con el formato *ruta*|*identificador* (por ejemplo, *File://ServerName/ Nombre de archivo/nombreCarpeta | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.  
  
     Para obtener más información acerca de cómo dar formato a este identificador, consulte [información general de las propiedades de documento personalizada](../vsto/custom-document-properties-overview.md).  
  
5.  Elija la **Aceptar** botón y, a continuación, guarde y cierre el documento.  
  
6.  Ejecute el programa de instalación sin el parámetro /url para instalar la solución en la ubicación especificada.  
  
##  <a name="Roll"></a> Revertir una solución a una versión anterior  
 Cuando se revierte una solución, se revierte a los usuarios a una versión anterior de la solución.  
  
#### <a name="to-roll-back-a-solution"></a>Para revertir una solución  
  
1.  Abra la ubicación de instalación de la solución.  
  
2.  Carpeta de publicación en el nivel superior, elimine el manifiesto de implementación (el *.vsto* archivo).  
  
3.  Busque la subcarpeta correspondiente a la versión a la que desea efectuar la reversión.  
  
4.  Copie el manifiesto de implementación de esa subcarpeta en la carpeta de publicación de nivel superior.  
  
     Por ejemplo, para revertir una solución que se llama **OutlookAddIn1** desde la versión 1.0.0.1 a la versión 1.0.0.0, copie el archivo **OutlookAddIn1.vsto** desde el **OutlookAddIn1_1_0_0_0** carpeta. Pegue el archivo en el nivel superior publicar la carpeta, sobrescribiendo el manifiesto de implementación específico de la versión **OutlookAddIn1_1_0_0_1** que ya estaba allí.  
  
     La ilustración siguiente muestra la estructura de carpetas de publicación de este ejemplo.  
  
     ![Publicar la estructura de carpetas](../vsto/media/publishfolderstructure.png "publicar la estructura de carpetas")  
  
     La próxima vez que un usuario abra la aplicación o el documento personalizado se detectará el cambio del manifiesto de implementación. La versión anterior de la solución de Office se ejecutará desde la caché de ClickOnce.  
  
> [!NOTE]  
>  Los datos locales se guardan para una sola versión anterior de una solución. Si revierte a dos versiones, no se conservan los datos locales. Para obtener más información sobre los datos locales, consulte [tener acceso a datos locales y remotos en aplicaciones ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="see-also"></a>Vea también  
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Publicar soluciones de Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Cómo: publicar una solución de Office mediante ClickOnce](http://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Cómo: instalar una solución de ClickOnce Office](http://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)   
 [Cómo: publicar una solución de Office de nivel de documento en un servidor de SharePoint mediante ClickOnce](http://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)   
 [Crear a un instalador personalizado para una solución de office ClickOnce](http://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)  
  
  
