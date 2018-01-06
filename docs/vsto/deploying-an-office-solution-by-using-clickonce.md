---
title: "Implementar una solución de Office mediante ClickOnce | Documentos de Microsoft"
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
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
ms.assetid: feb516b3-5e4d-449a-9fd2-347d08d90252
caps.latest.revision: "59"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0076eea1fa8866ad90bf4125583ed8359916de4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-an-office-solution-by-using-clickonce"></a>Implementar una solución de Office mediante ClickOnce
  Puede implementar su solución de Office en menos pasos si usa ClickOnce. Si publica actualizaciones, la solución las detectará e instalará automáticamente. Sin embargo, ClickOnce requiere que instale la solución por separado para cada usuario de un equipo. Por tanto, debería considerar usar Windows Installer (.msi) si más de un usuario ejecuta la solución en el mismo equipo.  
  
## <a name="in-this-topic"></a>En este tema  
  
-   [Publicar la solución](#Publish)  
  
-   [Decida cómo desea conceder confianza a la solución](#Trust)  
  
-   [Ayudar a los usuarios instalan la solución](#Helping)  
  
-   [Colocar el documento de una solución en el equipo del usuario final (solo para personalizaciones de nivel de documento)](#Put)  
  
-   [Colocar el documento de una solución en un servidor que ejecuta SharePoint (solo para personalizaciones de nivel de documento)](#SharePoint)  
  
-   [Crear a un instalador personalizado](#Custom)  
  
-   [Publicar una actualización](#Update)  
  
-   [Cambiar la ubicación de instalación de una solución](#Location)  
  
-   [Revertir una solución a una versión anterior](#Roll)  
  
 Para obtener más información sobre cómo implementar una solución de Office mediante la creación de un archivo de Windows Installer, consulte [implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Publish"></a>Publicar la solución  
 Puede publicar la solución mediante la **Asistente para publicación de** o **Diseñador de proyectos**. En este procedimiento, usará el **Diseñador de proyectos** porque proporciona el conjunto completo de opciones de publicación. Vea [publicar Asistente &#40; desarrollo de Office en Visual Studio &#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).  
  
#### <a name="to-publish-the-solution"></a>Para publicar la solución  
  
1.  En **el Explorador de soluciones**, elija el nodo que se denomina para el proyecto.  
  
2.  En la barra de menús, elija **proyecto**, *ProjectName* **propiedades**.  
  
3.  En el **Diseñador de proyectos**, elija la **publicar** ficha, que se muestra en la siguiente ilustración.  
  
     ![La pestaña publicar del Diseñador de proyectos](../vsto/media/vsto-publishtab.png "la pestaña publicar del Diseñador de proyectos")  
  
4.  En el **ubicación de la carpeta de publicación (servidor ftp o ruta de acceso de archivo)** cuadro, escriba la ruta de acceso de la carpeta donde desea que el **Diseñador de proyectos** para copiar los archivos de solución.  
  
     Puede especificar cualquiera de los siguientes tipos de rutas.  
  
    -   Una ruta de acceso local (por ejemplo, *C:\FolderName\FolderName*).  
  
    -   Una ruta de acceso de convención de nomenclatura universal (UNC) a una carpeta en la red (por ejemplo,  *\\\ServerName\FolderName*).  
  
    -   Ruta de acceso relativa (por ejemplo, *carpetaDePublicación\\*, que es la carpeta en la que se publica el proyecto de forma predeterminada).  
  
5.  En el **dirección URL de la carpeta de instalación** cuadro, escriba la ruta de acceso completa de la ubicación donde los usuarios finales encontrarán su solución.  
  
     Si no conoce la ubicación, no especifique nada en este campo. De forma predeterminada, ClickOnce busca actualizaciones en la carpeta en la que los usuarios instalan la solución.  
  
6.  Elija el botón **Requisitos previos** .  
  
7.  En el **requisitos previos** diálogo cuadro, asegúrese de que el **crear programa de instalación para instalar los componentes necesarios** casilla está activada.  
  
8.  En el **elegir los requisitos previos para instalar** , seleccione las casillas de verificación para **Windows Installer 4.5** y el paquete de .NET Framework adecuado.  
  
     Por ejemplo, si su solución tiene como destino el [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], active las casillas de verificación de **Windows Installer 4.5** y **Microsoft .NET Framework 4.5 completo**.  
  
9. Si la solución tiene como destino .NET Framework 4.5, también debe activar la **Visual Studio 2010 Tools para Office Runtime** casilla de verificación.  
  
    > [!NOTE]  
    >  De forma predeterminada, esta casilla de verificación no aparece. Para mostrar esta casilla, debe crear un paquete de programa previo. Vea [crear un paquete de arranque para un Office 2013 complemento de VSTO con Visual Studio 2012](http://blogs.msdn.com/b/vsto/archive/2012/12/21/creating-a-bootstrapper-package-for-an-office-2013-vsto-add-in-with-visual-studio-2012.aspx).  
  
10. En **especificar la ubicación de instalación de requisitos previos**, elija una de las opciones que aparecen y, a continuación, elijan la **Aceptar** botón.  
  
     En la siguiente tabla se describe cada una de las opciones.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |**Descargar los requisitos previos del sitio web del proveedor de los componentes**|Se pedirá al usuario que descargue e instale estos requisitos previos del proveedor.|  
    |**Descargar los requisitos previos de la misma ubicación que mi aplicación**|El software necesario se instala con la solución. Si elige esta opción, Visual Studio copia automáticamente todos los paquetes de requisitos previos en la ubicación de publicación. Para que esta opción funcione, los paquetes se deben encontrar en el equipo de desarrollo.|  
    |**Descargar los requisitos previos de la siguiente ubicación**|Visual Studio copia todos los paquetes de requisitos previos en la ubicación especificada y los instala con la solución.|  
  
     Vea [cuadro de diálogo de requisitos previos](/visualstudio/ide/reference/prerequisites-dialog-box).  
  
11. Elija la **actualizaciones** botón, especifique la frecuencia con desea que del cada usuario final complemento de VSTO o personalización para comprobar si hay actualizaciones y, a continuación, elija la **Aceptar** botón.  
  
    > [!NOTE]  
    >  Si va a implementar mediante un CD o una unidad extraíble, elija la **buscar nunca actualizaciones** botón de opción.  
  
     Para obtener información sobre cómo publicar una actualización, vea [publicar una actualización](#Update).  
  
12. Elija la **opciones** botón, revise las opciones en el **opciones** diálogo cuadro y, a continuación, elija la **Aceptar** botón.  
  
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
    >  ClickOnce anexa la extensión .deploy a los ensamblados para que una instalación segura de Internet Information Services (IIS) no bloquee los archivos debido a una extensión no segura. Cuando el usuario instale la solución, ClickOnce quitará la extensión .deploy.  
  
14. Copie los archivos de la solución en la ubicación de instalación especificada anteriormente en este procedimiento.  
  
##  <a name="Trust"></a>Decida cómo desea conceder confianza a la solución  
 Para que una solución pueda ejecutarse en los equipos de los usuarios, debe conceder confianza o los usuarios deben responder al mensaje relativo a la confianza cuando instalen la solución. Para conceder confianza a la solución, firme los manifiestos mediante un certificado que identifique un publicador de confianza conocido. Vea [manifiestos de confiar en la solución mediante la firma de la aplicación e implementación](../vsto/granting-trust-to-office-solutions.md#Signing).  
  
 Si va a implementar una personalización de nivel de documento y desea colocar el documento en una carpeta en el equipo del usuario o hacer que el documento esté disponible en un sitio de SharePoint, asegúrese de que Office confíe en la ubicación del documento. Vea [otorgar confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
##  <a name="Helping"></a>Ayudar a los usuarios instalan la solución  
 Los usuarios pueden instalar la solución ejecutando el programa de instalación, abriendo el manifiesto de implementación o, en el caso de una personalización de nivel de documento, abriendo el documento directamente. El procedimiento recomendado es que los usuarios instalen la solución mediante el programa de instalación. Los otros dos enfoques no garantizan que el software necesario está instalado. Si los usuarios desean abrir el documento desde la ubicación de instalación, deben agregarlo a la lista de ubicaciones de confianza en el Centro de confianza de la aplicación de Office.  
  
### <a name="opening-the-document-of-a-document-level-customization"></a>Abrir el documento de una personalización de nivel de documento  
 Los usuarios pueden abrir el documento de una personalización de nivel de documento directamente desde la ubicación de instalación o copiando el documento en el equipo local y después abriendo la copia.  
  
 Como procedimiento recomendado, los usuarios deben abrir una copia del documento en sus equipos para impedir que varios usuarios intenten abrir la misma copia al mismo tiempo. Para aplicar esta práctica recomendada, puede configurar el programa de instalación de forma que copie el documento en los equipos de los usuarios. Vea [colocar el documento de una solución en el equipo del usuario final (solo para personalizaciones de nivel de documento)](#Put).  
  
### <a name="installing-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Instalar la solución abriendo el manifiesto de implementación desde un sitio web de IIS  
 Los usuarios pueden instalar una solución de Office abriendo el manifiesto de implementación desde la Web. Sin embargo, una instalación segura de Internet Information Services (IIS) bloqueará los archivos que tengan la extensión .vsto. El tipo MIME se debe definir en IIS para poder implementar una solución de Office mediante IIS.  
  
##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Para agregar el tipo MIME .vsto a IIS 6.0  
  
1.  En el servidor que está ejecutando IIS 6.0, elija **iniciar**, **todos los programas**, **herramientas administrativas**, **elAdministradordeInternetInformationServices(IIS)**.  
  
2.  Elija el nombre del equipo, el **sitios Web** carpeta o el sitio web que está configurando.  
  
3.  En la barra de menús, elija **acción**, **propiedades**.  
  
4.  En el **encabezados HTTP** ficha, elija la **tipos MIME** botón.  
  
5.  En el **tipos MIME** ventana, elija la **New** botón.  
  
6.  En el **tipo MIME** ventana, escriba **.vsto** la extensión, escriba **application/x-ms-vsto** como MIME escriba y, a continuación, aplicar la nueva configuración.  
  
    > [!NOTE]  
    >  Para que los cambios surtan efecto, debe reiniciar el Servicio de publicación World Wide Web o esperar hasta que el proceso de trabajo se recicle. Debe vaciar la memoria caché del disco del explorador y después intentar abrir de nuevo el archivo .vsto.  
  
##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Para agregar el tipo MIME .vsto a IIS 7,0  
  
1.  En el servidor que ejecuta IIS 7.0, elija **iniciar**, **todos los programas**, **Accesorios**.  
  
2.  Abra el menú contextual para **símbolo**y, a continuación, elija **ejecutar como administrador.**  
  
3.  En el **abiertos** cuadro, escriba la ruta de acceso siguiente y, a continuación, elija la **Aceptar** botón.  
  
    ```  
    %windir%\system32\inetsrv   
    ```  
  
4.  Escriba el comando siguiente y, a continuación, aplique la nueva configuración.  
  
    ```  
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  
  
    > [!NOTE]  
    >  Para que los cambios surtan efecto, debe reiniciar el Servicio de publicación World Wide Web o debe esperar hasta que el proceso de trabajo se recicle. Debe vaciar la memoria caché del disco del explorador y después intentar abrir de nuevo el archivo .vsto.  
  
##  <a name="Put"></a>Colocar el documento de una solución en el equipo del usuario final (solo para personalizaciones de nivel de documento)  
 Puede copiar el documento de la solución en el equipo del usuario final para ellos mediante la creación de una acción posterior a la implementación. De este modo, el usuario no tiene que copiar manualmente el documento desde la ubicación de instalación en su equipo después de instalar la solución. Tendrá que crear una clase que defina la acción posterior a la implementación, compilar y publicar la solución, modificar el manifiesto de aplicación y volver a firmar el manifiesto de aplicación e implementación.  
  
 Los procedimientos siguientes suponen que es el nombre del proyecto **ExcelWorkbook** y publicar la solución para la **C:\publish** directorio en el equipo.  
  
### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Crear una clase que defina la acción posterior a la implementación  
  
1.  En la barra de menús, elija **Archivo**, **Agregar**, **Nuevo proyecto**.  
  
2.  En el **Agregar nuevo proyecto** cuadro de diálogo, en la **plantillas instaladas** panel, elija la **Windows** carpeta.  
  
3.  En el **plantillas** panel, elija la **biblioteca de clases** plantilla.  
  
4.  En el **nombre** , escriba **FileCopyPDA**y, a continuación, elija la **Aceptar** botón.  
  
5.  En **el Explorador de soluciones**, elija la **FileCopyPDA** proyecto.  
  
6.  En la barra de menús, elija **Proyecto**, **Agregar referencia**.  
  
7.  En el **.NET** ficha, agregue referencias a Microsoft.VisualStudio.Tools.Applications.Runtime y Microsoft.VisualStudio.Tools.Applications.ServerDocument.  
  
8.  Cambie el nombre de la clase a `FileCopyPDA` y reemplace el contenido del archivo con el código. Este código realiza las tareas siguientes:  
  
    -   Copia el documento en el escritorio del usuario.  
  
    -   Cambia la propiedad _AssemblyLocation desde una ruta de acceso relativa a una ruta de acceso completa para el manifiesto de implementación.  
  
    -   Elimina el archivo si el usuario desinstala la solución.  
  
     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]  
  
### <a name="build-and-publish-the-solution"></a>Compilar y publicar la solución  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **FileCopyPDA** del proyecto y, a continuación, elija **generar**.  
  
2.  Abra el menú contextual para el **ExcelWorkbook** del proyecto y, a continuación, elija **generar**.  
  
3.  Abra el menú contextual para el **ExcelWorkbook** del proyecto y, a continuación, elija **Agregar referencia**.  
  
4.  En el **Agregar referencia** diálogo cuadro, elija la **proyectos** ficha, elija **FileCopyPDA**y, a continuación, elija la **Aceptar** botón.  
  
5.  En **el Explorador de soluciones**, elija la **ExcelWorkbook** proyecto.  
  
6.  En la barra de menús, elija **proyecto**, **nueva carpeta**.  
  
7.  ENTRAR **datos**y, a continuación, elija la tecla ENTRAR.  
  
8.  En **el Explorador de soluciones**, elija la **datos** carpeta.  
  
9. En la barra de menús, elija **proyecto**, **Agregar elemento existente**.  
  
10. En el **Agregar elemento existente** cuadro de diálogo, desplácese hasta el directorio de salida para el **ExcelWorkbook** proyecto, elija la **ExcelWorkbook.xlsx** de archivos y, a continuación, elija la  **Agregar** botón.  
  
11. En **el Explorador de soluciones** elegir el **ExcelWorkbook.xlsx** archivo.  
  
12. En el **propiedades** ventana, cambiar el **acción de compilación** propiedad **contenido** y **copiar en el directorio de salida** propiedad  **Copiar si es posterior**.  
  
     Cuando haya completado estos pasos, el proyecto asemejará a la siguiente ilustración.  
  
     ![Estructura de proyecto de la acción posterior a la implementación. ] (../vsto/media/vsto-postdeployment.png "Estructura de proyecto de la acción posterior a la implementación.")  
  
13. Publicar la **ExcelWorkbook** proyecto.  
  
### <a name="modify-the-application-manifest"></a>Modificar el manifiesto de aplicación  
  
1.  Abra la **c:\publish** directorio mediante el uso de **Explorador de archivos**.  
  
2.  Abra la **archivos de la aplicación** carpeta y, a continuación, abra la carpeta que corresponde a la última versión publicada de la solución.  
  
3.  Abra la **ExcelWorkbook.dll.manifest** archivo en un editor de texto como Bloc de notas.  
  
4.  Agregue el código siguiente detrás del elemento `</vstav3:update>`. El atributo de clase de la `<vstav3:entryPoint>` elemento, use la siguiente sintaxis: *nombreDeEspacioDeNombres.nombreDeClase*. En el ejemplo siguiente, los nombres de clase y espacio de nombres son los mismos, por lo que el nombre del punto de entrada resultante es `FileCopyPDA.FileCopyPDA`.  
  
    ```  
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
  
2.  Abra el símbolo del sistema de Visual Studio y, a continuación, cambie los directorios a la **c:\publish\Application aplicación\excelworkbook**\__Versiónpublicadamásreciente_ carpeta (por ejemplo, **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).  
  
3.  Firme el manifiesto de aplicación modificado ejecutando el siguiente comando:  
  
    ```  
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  
  
     Aparece el mensaje "ExcelWorkbook.dll.manifest firmado correctamente".  
  
4.  Cambie a la **c:\publish** carpeta y, a continuación, actualización y la implementación del inicio de sesión de manifiesto ejecutando el comando siguiente:  
  
    ```  
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  
  
    > [!NOTE]  
    >  En el ejemplo anterior, reemplace MostRecentVersionNumber con el número de versión de la versión publicada más recientemente de la solución (por ejemplo, **1_0_0_4**).  
  
     Aparece el mensaje "ExcelWorkbook.vsto firmado correctamente".  
  
5.  Copie el archivo ExcelWorkbook.vsto en el **c:\publish\Application aplicación\excelworkbook**\__Versiónpublicadamásreciente_ directory.  
  
##  <a name="SharePoint"></a>Colocar el documento de una solución en un servidor que ejecuta SharePoint (solo para personalizaciones de nivel de documento)  
 Puede publicar la personalización de nivel de documento para los usuarios finales mediante SharePoint. Cuando los usuarios van al sitio de SharePoint y abren el documento, el runtime instala automáticamente la solución desde la carpeta de red compartida en el equipo local del usuario. Una vez instalada localmente la solución, la personalización seguirá funcionando aunque el documento se copie en otra parte, como el escritorio.  
  
#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Para colocar el documento en un servidor que ejecuta SharePoint  
  
1.  Agregue el documento de la solución a una biblioteca de documentos en un sitio de SharePoint.  
  
2.  Siga los pasos de alguno de estos enfoques:  
  
    -   Utilice la herramienta de configuración de Office para agregar el servidor que ejecuta SharePoint al Centro de confianza de Word o Excel en todos los equipos de los usuarios.  
  
         Vea [directivas de seguridad y la configuración de Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).  
  
    -   Asegúrese de que cada usuario realice los pasos siguientes.  
  
        1.  En el equipo local, abra Word o Excel, elija la **archivo** ficha y, a continuación, elija la **opciones** botón.  
  
        2.  En el **centro de confianza** diálogo cuadro, elija la **ubicaciones de confianza** botón.  
  
        3.  Seleccione el **Permitir ubicaciones de confianza en la red (no recomendado)** casilla de verificación y, a continuación, elija la **agregar nueva ubicación** botón.  
  
        4.  En el **ruta de acceso** cuadro, escriba la dirección URL de la biblioteca de documentos de SharePoint que contiene el documento cargado (por ejemplo, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).  
  
             No agregue el nombre de la página Web predeterminada, como default.aspx o AllItems.aspx.  
  
        5.  Seleccione el **las subcarpetas de esta ubicación también son de confianza** casilla de verificación y, a continuación, elija la **Aceptar** botón.  
  
             Cuando los usuarios abran el documento desde el sitio de SharePoint, se abrirá el documento y se instalará la personalización. Los usuarios pueden copiar el documento en el escritorio. La personalización se ejecutará igualmente porque las propiedades del documento apuntan a la ubicación de red del documento.  
  
##  <a name="Custom"></a>Crear a un instalador personalizado  
 Puede crear a un instalador personalizado para la solución de Office, en lugar de usar el programa de instalación que se crea automáticamente cuando se publica la solución. Por ejemplo, podría usar un script de inicio de sesión para iniciar la instalación o podría usar un archivo por lotes para instalar la solución sin interacción del usuario. Estos escenarios funcionan mejor si los requisitos previos ya están instalados en los equipos de los usuarios finales.  
  
 Como parte del proceso de instalación personalizada, llame a la herramienta de instalación de soluciones de Office (VSTOInstaller.exe), que se instala en la siguiente ubicación de forma predeterminada:  
  
 %commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe  
  
 Si la herramienta no está en esa ubicación, puede usar la clave del Registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath o HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath para encontrar la ruta de acceso a esa herramienta.  
  
 Puede utilizar los siguientes parámetros con VSTOinstaller.exe.  
  
|Parámetro|Definición|  
|---------------|----------------|  
|/Install o /I|Instala la solución. Esta opción debe ir seguida de la ruta de acceso de un manifiesto de implementación. Puede especificar una ruta de acceso en el equipo local —un recurso compartido de archivos de convención de nomenclatura universal (UNC)—. Puede especificar una ruta de acceso local (*C:\FolderName\PublishFolder*), una ruta de acceso relativa (*publicar\\*), o una ubicación completa (*\\\ServerName\ NombreDeCarpeta* o http://*nombreDeServidor/nombreDeCarpeta*).|  
|/Uninstall o /U|Desinstala la solución. Esta opción debe ir seguida de la ruta de acceso de un manifiesto de implementación. Puede especificar que una ruta de acceso puede estar en el equipo local, en un recurso compartido de archivos UNC. Puede especificar una ruta de acceso local (*c:\FolderName\PublishFolder*), una ruta de acceso relativa (*publicar\\*), o una ubicación completa (*\\\ServerName\ NombreDeCarpeta* o http://*nombreDeServidor/nombreDeCarpeta*).|  
|/Silent o /S|Instala o desinstala sin solicitar la entrada de datos del usuario ni mostrar ningún mensaje. Si se requiere una confirmación de confianza, la personalización no está instalada o actualizada.|  
|/Help o /?|Muestra la información de Ayuda.|  
  
 Cuando ejecute VSTOinstaller.exe, pueden aparecer los códigos de error siguientes.  
  
|Código de error|Definición|  
|----------------|----------------|  
|0|La solución se instaló o desinstaló correctamente o se mostró la Ayuda de VSTOInstaller.|  
|-100|Una o más opciones de la línea de comandos no son válidas o se establecieron más de una vez. Para obtener más información, escriba "¿vstoinstaller /?" o vea [crear un instalador personalizado para una solución de Office ClickOnce](http://msdn.microsoft.com/en-us/3e5887ed-155f-485d-b8f6-3c02c074085e).|  
|-101|Una o varias opciones de línea de comandos no es válido. Para obtener más información, escriba “vstoinstaller/?”.|  
|-200|El URI del manifiesto de implementación no es válido. Para obtener más información, escriba “vstoinstaller/?”.|  
|-201|No se pudo instalar la solución porque el manifiesto de implementación no es válido. Vea [manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md).|  
|-202|No se pudo instalar la solución porque Visual Studio Tools para la sección de Office del manifiesto de aplicación no es válida. Vea [manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md).|  
|-203|No se pudo instalar la solución porque se produjo un error de descarga. Compruebe el URI o la ubicación del archivo de red del manifiesto de implementación e inténtelo de nuevo.|  
|-300|No se pudo instalar la solución porque se produjo una excepción de seguridad. Vea [asegurar las soluciones de Office](../vsto/securing-office-solutions.md).|  
|-400|No se pudo instalar la solución.|  
|-401|No se pudo desinstalar la solución.|  
|-500|Se ha cancelado la operación porque no se pudo instalar o desinstalar la solución o porque no se pudo descargar el manifiesto de implementación.|  
  
##  <a name="Update"></a>Publicar una actualización  
 Para actualizar una solución, publíquela de nuevo mediante el uso de la **Diseñador de proyectos** o **Asistente para publicación**, y, a continuación, copie la solución actualizada a la ubicación de instalación. Cuando copie los archivos en la ubicación de instalación, asegúrese de sobrescribir los archivos anteriores.  
  
 La próxima vez que la solución comprueba una actualización, que podrá encontrar y cargar la nueva versión automáticamente.  
  
##  <a name="Location"></a>Cambiar la ubicación de instalación de una solución  
 Puede agregar o cambiar la ruta de instalación después de publicar una solución. Puede cambiar la ruta de instalación por alguna de las siguientes razones:  
  
-   El programa de instalación se compiló antes de que se conociera la ruta de instalación.  
  
-   Los archivos de la solución se han copiado en otra ubicación.  
  
-   El servidor que hospeda los archivos de instalación tiene un nombre o una ubicación nuevos.  
  
 Para cambiar la ruta de instalación de una solución, debe actualizar el programa de instalación. Los usuarios tendrán que ejecutar este programa. Para las personalizaciones de nivel de documento, los usuarios también deben actualizar una propiedad en el documento para que apunte a la nueva ubicación.  
  
> [!NOTE]  
>  Si no desea pedir a los usuarios que actualicen las propiedades de documento, puede pedir a los usuarios obtengan el documento actualizado de la ubicación de instalación.  
  
#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Para cambiar la ruta de instalación en el programa de instalación  
  
1.  Abra un **símbolo** ventana y, a continuación, cambie los directorios a la carpeta de instalación.  
  
2.  Ejecute el programa de instalación e incluya el parámetro `/url`, que toma la nueva ruta de instalación como una cadena.  
  
     En el ejemplo siguiente se muestra cómo cambiar la ruta de instalación a una ubicación del sitio web de Fabrikam, pero puede reemplazar esa dirección URL por la ruta que desee:  
  
    ```  
    setup.exe /url="http://www.fabrikam.com/newlocation"  
    ```  
  
    > [!NOTE]  
    >  Si aparece un mensaje y se indica que la firma del archivo ejecutable se va a invalidar, el certificado utilizado para firmar la solución ya no es válido y se desconoce el publicador. Como resultado, los usuarios deberán confirmar que confían en el origen de la solución para poder instalarla.  
  
    > [!NOTE]  
    >  Para mostrar el valor actual de la dirección URL, ejecute `setup.exe /url`.  
  
 Para las personalizaciones de nivel de documento, los usuarios deben abrir el documento y, a continuación, actualice la propiedad _AssemblyLocation. Los pasos siguientes describen cómo los usuarios pueden realizar esta tarea.  
  
#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>Para actualizar la propiedad _AssemblyLocation en un documento  
  
1.  En el **archivo** ficha, elija **información**, que se muestra en la siguiente ilustración.  
  
     ![Ficha información en Excel](../vsto/media/vsto-infotab.png "pestaña información de Excel")  
  
2.  En el **propiedades** elija **propiedades avanzadas**, que se muestra en la siguiente ilustración.  
  
     ![Propiedades avanzadas de Excel. ] (../vsto/media/vsto-advanceddocumentproperties.png "Propiedades avanzadas en Excel.")  
  
3.  En el **personalizado** pestaña en el **propiedades** elija _AssemblyLocation, tal como se muestra en la ilustración siguiente.  
  
     ![La propiedad AssemblyLocation. ] (../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation la propiedad.")  
  
     El **valor** cuadro contiene el identificador del manifiesto de implementación.  
  
4.  Delante del identificador, escriba la ruta de acceso completa del documento, seguido de una barra, con el formato *ruta de acceso*|*identificador* (por ejemplo, *File://ServerName/ NombreDeCarpeta/FileName | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.  
  
     Para obtener más información acerca de cómo dar formato a este identificador, consulte [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md).  
  
5.  Elija la **Aceptar** botón y, a continuación, guarde y cierre el documento.  
  
6.  Ejecute el programa de instalación sin el parámetro /url para instalar la solución en la ubicación especificada.  
  
##  <a name="Roll"></a>Revertir una solución a una versión anterior  
 Cuando se revierte una solución, se revierte a los usuarios a una versión anterior de la solución.  
  
#### <a name="to-roll-back-a-solution"></a>Para revertir una solución  
  
1.  Abra la ubicación de instalación de la solución.  
  
2.  En la carpeta de publicación de nivel superior, elimine el manifiesto de implementación (el archivo .vsto).  
  
3.  Busque la subcarpeta correspondiente a la versión a la que desea efectuar la reversión.  
  
4.  Copie el manifiesto de implementación de esa subcarpeta en la carpeta de publicación de nivel superior.  
  
     Por ejemplo, para revertir una solución que se llama **OutlookAddIn1** desde la versión 1.0.0.1 a la versión 1.0.0.0, copie el archivo **OutlookAddIn1.vsto** desde el **OutlookAddIn1_1_0_0_0** carpeta. Pegue el archivo en la carpeta de publicación, sobrescribiendo el manifiesto de implementación específico de la versión de **OutlookAddIn1_1_0_0_1** que ya estaba allí.  
  
     La ilustración siguiente muestra la estructura de carpetas de publicación de este ejemplo.  
  
     ![Publicar la estructura de carpetas](../vsto/media/publishfolderstructure.png "publicar la estructura de carpetas")  
  
     La próxima vez que un usuario abra la aplicación o el documento personalizado se detectará el cambio del manifiesto de implementación. La versión anterior de la solución de Office se ejecutará desde la caché de ClickOnce.  
  
> [!NOTE]  
>  Los datos locales se guardan para una sola versión anterior de una solución. Si se revierte dos versiones, no se conservan datos locales. Para obtener más información acerca de los datos locales, consulte [obtener acceso Local y remoto datos en aplicaciones ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="see-also"></a>Vea también  
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Publicar soluciones de Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Cómo: publicar una solución de Office mediante ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Cómo: instalar una solución de Office ClickOnce](http://msdn.microsoft.com/en-us/14702f48-9161-4190-994c-78211fe18065)   
 [Cómo: publicar una solución de Office de nivel de documento en un servidor de SharePoint mediante ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58)   
 [Crear a un instalador personalizado para una solución de Office ClickOnce](http://msdn.microsoft.com/en-us/3e5887ed-155f-485d-b8f6-3c02c074085e)  
  
  
