---
title: 'Tutorial: Implementar manualmente una aplicación ClickOnce | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71ab59e09f450d1656d77c551b3f44d0a60f1a57
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Tutorial: Implementar manualmente una aplicación ClickOnce
Si no se puede usar Visual Studio para implementar su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, o si necesita usar características de implementación avanzada, como la implementación de aplicaciones de confianza, debe usar la herramienta de línea de comandos Mage.exe para crear su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiestos. Este tutorial describe cómo crear un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación mediante el uso de la versión de línea de comandos (Mage.exe) o la versión gráfica (MageUI.exe) de la herramienta de edición y generación de manifiestos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 En este tutorial tiene algunos requisitos previos y las opciones que debe elegir antes de compilar una implementación.  
  
-   Instale Mage.exe y MageUI.exe.  
  
     Mage.exe y MageUI.exe forman parte de la [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Debe tener la [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] instalado o la versión de la [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] incluidos con Visual Studio. Para obtener más información, consulte [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) en MSDN.  
  
-   Proporcionar una aplicación para la implementación.  
  
     En este tutorial se da por supuesto que tiene una aplicación de Windows que esté listo para implementar. Esta aplicación se denominará AppToDeploy.  
  
-   Determine cómo se distribuirá la implementación.  
  
     Las opciones de distribución incluyen: Web, recurso compartido de archivos o CD. Para obtener más información, consulta [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
-   Determine si la aplicación requiere un nivel elevado de confianza.  
  
     Si la aplicación requiere plena confianza, por ejemplo, acceso total al sistema del usuario, puede usar el `-TrustLevel` opción de Mage.exe para establecer esto. Si desea definir un permiso personalizado establecido para la aplicación, puede copiar la sección de permisos de Internet o intranet de otro manifiesto, modificarlo para adecuarlo a sus necesidades y agregarlo al manifiesto de aplicación mediante un editor de texto o MageUI.exe. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
-   Obtenga un certificado de Authenticode.  
  
     Debe firmar la implementación con un certificado Authenticode. Puede generar un certificado de prueba mediante las herramientas de Visual Studio, MageUI.exe o MakeCert.exe y Pvk2Pfx.exe o puede obtener un certificado de una entidad de certificación (CA). Si decide usar la implementación de aplicaciones de confianza, también debe realizar una instalación única del certificado en todos los equipos cliente. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    >  También puede firmar la implementación con un certificado CNG que puede obtener de una entidad de certificación.  
  
-   Asegúrese de que la aplicación no tiene un manifiesto con información de UAC.  
  
     Debe determinar si la aplicación contiene un manifiesto con información de Control de cuentas de usuario (UAC), como un `<dependentAssembly>` elemento. Para examinar un manifiesto de aplicación, puede usar Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) utilidad.  
  
     Si la aplicación contiene un manifiesto con detalles UAC, debe volver a generar sin la información de UAC. Para un proyecto de C# en Visual Studio, abra las propiedades del proyecto y seleccione la pestaña aplicación. En el **manifiesto** lista desplegable, seleccione **crear aplicación sin manifiesto**. Para un proyecto de Visual Basic en Visual Studio, abra las propiedades del proyecto, seleccione la pestaña aplicación y haga clic en **ver configuración de UAC**. En el archivo de manifiesto abierto, quite todos los elementos dentro de la única `<asmv1:assembly>` elemento.  
  
-   Determinar si la aplicación requiere que los requisitos previos en el equipo cliente.  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones implementadas desde Visual Studio pueden incluir un instalación de requisitos previos del programa previo (setup.exe) con la implementación. Este tutorial crea los dos manifiestos requeridos para una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación. Puede crear un arranque de requisitos previos mediante el [GenerateBootstrapper (tarea)](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Para implementar una aplicación con la herramienta de línea de comandos Mage.exe  
  
1.  Cree un directorio donde se almacenarán los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos de implementación.  
  
2.  En el directorio de implementación que acaba de crear, cree un subdirectorio de la versión. Si se trata de la primera vez que va a implementar la aplicación, el nombre del subdirectorio de la versión **1.0.0.0**.  
  
    > [!NOTE]
    >  La versión de la implementación puede ser distinta de la versión de la aplicación.  
  
3.  Copie todos los archivos de aplicación en el subdirectorio de versión, incluidos los archivos ejecutables, ensamblados, recursos y archivos de datos. Si es necesario, puede crear subdirectorios adicionales que contienen archivos adicionales.  
  
4.  Abra el [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] o un comando de Visual Studio símbolo del sistema y cambie al subdirectorio de versión.  
  
5.  Crear el manifiesto de aplicación con una llamada a Mage.exe. La siguiente instrucción crea un manifiesto de aplicación para el código compilado para ejecutarse en el procesador Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  No olvide incluir el punto (.) después de la `-FromDirectory` opción, que indica el directorio actual. Si no incluye el punto, debe especificar la ruta de acceso a los archivos de aplicación.  
  
6.  Firme el manifiesto de aplicación con el certificado Authenticode. Reemplace *mycert.pfx* con la ruta de acceso al archivo de certificado. Reemplace *passwd* con la contraseña para el archivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Para firmar el manifiesto de aplicación con un certificado CNG, utilice lo siguiente. Reemplace *cngCert.pfx* con la ruta de acceso al archivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  Cambie a la raíz del directorio de implementación.  
  
8.  Generar el manifiesto de implementación con una llamada a Mage.exe. De forma predeterminada, Mage.exe marcará la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación como una aplicación instalada, por lo que TI puede ejecutarse tanto en línea y sin conexión. Para que la aplicación esté disponible solo cuando el usuario está en línea, use la `-Install` opción con un valor de `false`. Si usa el valor predeterminado, y los usuarios instalarán la aplicación desde un sitio Web o recurso compartido de archivos, asegúrese de que el valor de la `-ProviderUrl` puntos de opción a la ubicación de la aplicación del manifiesto en el servidor Web o recurso compartido.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Firme el manifiesto de implementación con el certificado Authenticode o CNG.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     o  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Copie todos los archivos en el directorio de implementación en el destino de la implementación o el medio. Esto puede ser una carpeta en un sitio Web o sitio FTP, un recurso compartido de archivos o un CD-ROM.  
  
11. Proporcionar a los usuarios con el medio físico, debe instalar la aplicación, dirección URL o UNC. Si proporciona una dirección URL o una ruta UNC, debe ofrecer a los usuarios la ruta de acceso completa al manifiesto de implementación. Por ejemplo, si se implementa AppToDeploy en http://webserver01/ en el directorio AppToDeploy, la ruta de acceso de dirección URL completa sería http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Para implementar una aplicación con la herramienta gráfica MageUI.exe  
  
1.  Cree un directorio donde se almacenarán los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos de implementación.  
  
2.  En el directorio de implementación que acaba de crear, cree un subdirectorio de la versión. Si se trata de la primera vez que va a implementar la aplicación, el nombre del subdirectorio de la versión **1.0.0.0**.  
  
    > [!NOTE]
    >  La versión de la implementación probablemente es distinta de la versión de la aplicación.  
  
3.  Copie todos los archivos de aplicación en el subdirectorio de versión, incluidos los archivos ejecutables, ensamblados, recursos y archivos de datos. Si es necesario, puede crear subdirectorios adicionales que contienen archivos adicionales.  
  
4.  Inicie la herramienta gráfica MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Crear un nuevo manifiesto de aplicación seleccionando **archivo**, **New**, **Application Manifest** en el menú.  
  
6.  En el valor predeterminado **nombre** ficha, escriba el nombre y número de versión de esta implementación. Especifique también la **procesador** que se creó la aplicación, como x86.  
  
7.  Seleccione el **archivos** ficha y haga clic en el botón de puntos suspensivos (**...** ) situado junto a la **directorio de la aplicación** cuadro de texto. Aparece un cuadro de diálogo Buscar carpeta.  
  
8.  Seleccione el subdirectorio de la versión que contiene los archivos de aplicación y, a continuación, haga clic en **Aceptar**.  
  
9. Si va a implementar servicios de Internet Information Server (IIS), seleccione la **al rellenar agregar la extensión .deploy a cualquier archivo que no tenga** casilla de verificación.  
  
10. Haga clic en el **rellenar** botón para agregar todos los archivos de aplicación a la lista de archivos. Si la aplicación contiene más de un archivo ejecutable, marque el archivo ejecutable principal de esta implementación como la aplicación de inicio seleccionando **punto de entrada** desde el **tipo de archivo** lista desplegable. (Si la aplicación contiene un único archivo ejecutable, MageUI.exe lo marcará para usted.)  
  
11. Seleccione el **permisos necesarios** pestaña y seleccione el nivel de confianza que la aplicación necesita imponer. El valor predeterminado es **FullTrust**, que será adecuado para la mayoría de las aplicaciones.  
  
12. Seleccione **archivo**, **Guardar como** en el menú. Aparece un cuadro de diálogo de opciones de firma que le pide que firme el manifiesto de aplicación.  
  
13. Si tiene un certificado almacenado como un archivo en el sistema de archivos, use la **firmar con archivo de certificado** opción y seleccione el certificado en el sistema de archivos mediante el uso de los puntos suspensivos (**...** ) botón. A continuación, escriba la contraseña del certificado.  
  
     -o bien-  
  
     Si el certificado se guarda en un almacén de certificados accesible desde el equipo, seleccione la **firmar con certificado almacenado** opción y seleccione el certificado de la lista proporcionada.  
  
14. Haga clic en **Aceptar** para firmar el manifiesto de aplicación. Aparecerá el cuadro de diálogo Guardar como.  
  
15. En el cuadro de diálogo Guardar como, especifique el directorio de la versión y, a continuación, haga clic en **guardar**.  
  
16. Seleccione **archivo**, **New**, **manifiesto de implementación** en el menú para crear el manifiesto de implementación.  
  
17. En el **nombre** ficha, especifique un nombre y número de versión para esta implementación (**1.0.0.0** en este ejemplo). Especifique también la **procesador** que se creó la aplicación, como x86.  
  
18. Seleccione el **descripción** pestaña y especificar los valores de **Publisher** y **Produc *** t**. (**Producto** es el nombre dado a la aplicación en el menú Inicio de Windows cuando se instala la aplicación en un equipo cliente para su uso sin conexión.)  
  
19. Seleccione el **opciones de implementación** ficha y en el **iniciar ubicación** texto, especifique la ubicación del manifiesto de aplicación en el servidor Web o recurso compartido. Por ejemplo, \\\myServer\myShare\AppToDeploy.application.  
  
20. Si ha agregado la extensión .deploy en un paso anterior, seleccione también **usar la extensión de nombre de archivo .deploy** aquí.  
  
21. Seleccione el **opciones de actualización** pestaña y especificar la frecuencia con la desea que esta aplicación para actualizar. Si la aplicación utiliza <xref:System.Deployment.Application.UpdateCheckInfo> para comprobar las actualizaciones, desactive la **esta aplicación debe buscar actualizaciones** casilla de verificación.  
  
22. Seleccione el **referencia de la aplicación** ficha y, a continuación, haga clic en el **Seleccionar manifiesto** botón. Aparece un cuadro de diálogo Abrir.  
  
23. Seleccione el manifiesto de aplicación que creó anteriormente y, a continuación, haga clic en **abiertos**.  
  
24. Seleccione **archivo**, **Guardar como** en el menú. Aparece un cuadro de diálogo de opciones de firma que le pide que firme el manifiesto de implementación.  
  
25. Si tiene un certificado almacenado como un archivo en el sistema de archivos, use la **firmar con archivo de certificado** opción y seleccione el certificado en el sistema de archivos mediante el uso de los puntos suspensivos (**...** ) botón. A continuación, escriba la contraseña del certificado.  
  
     -o bien-  
  
     Si el certificado se guarda en un almacén de certificados accesible desde el equipo, seleccione la **firmar con certificado almacenado** opción y seleccione el certificado de la lista proporcionada.  
  
26. Haga clic en **Aceptar** para firmar el manifiesto de implementación. Aparecerá el cuadro de diálogo Guardar como.  
  
27. En el **Guardar como** Subir un directorio a la raíz de la implementación y, a continuación, haga clic en el cuadro de diálogo **guardar**.  
  
28. Copie todos los archivos en el directorio de implementación en el destino de la implementación o el medio. Esto puede ser una carpeta en un sitio Web o sitio FTP, un recurso compartido de archivos o un CD-ROM.  
  
29. Proporcionar a los usuarios con el medio físico, debe instalar la aplicación, dirección URL o UNC. Si proporciona una dirección URL o una ruta UNC, debe ofrecer a los usuarios la ruta de acceso completa al manifiesto de implementación. Por ejemplo, si se implementa AppToDeploy en http://webserver01/ en el directorio AppToDeploy, la ruta de acceso de dirección URL completa sería http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Cuando necesite implementar una nueva versión de la aplicación, cree un nuevo directorio con el nombre de la nueva versión, por ejemplo, 1.0.0.1 copiar los nuevos archivos de aplicación en el nuevo directorio. A continuación, debe seguir los pasos anteriores para crear y firmar un manifiesto de aplicación nuevo y actualizar y firmar el manifiesto de implementación. Tenga cuidado de especificar la misma versión superior en ambos Mage.exe `-New` y `-Update` llamadas, como [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] solo actualiza las versiones posteriores, con el entero del extremo izquierdo más significativo. Si ha usado MageUI.exe, puede actualizar el manifiesto de implementación, ábralo, seleccione la **referencia de la aplicación** ficha, haga clic en el **Seleccionar manifiesto** botón y, a continuación, seleccionando la actualización manifiesto de aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)