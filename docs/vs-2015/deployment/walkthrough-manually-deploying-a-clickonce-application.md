---
title: 'Tutorial: implementar manualmente una aplicación ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e1099eaf8d766088612abbb399bdf004e6378e4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294677"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Tutorial: Implementar manualmente una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si no puede usar Visual Studio para implementar la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] o necesita usar características de implementación avanzadas, como la implementación de aplicaciones de confianza, debe usar la herramienta de línea de comandos Mage. exe para crear los manifiestos de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. En este tutorial se describe cómo crear una implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mediante la versión de línea de comandos (Mage. exe) o la versión gráfica (MageUI. exe) del Herramienta de generación y edición de manifiestos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Este tutorial tiene algunos requisitos previos y opciones que debe elegir antes de compilar una implementación.  
  
- Instale Mage. exe y MageUI. exe.  
  
     Mage. exe y MageUI. exe forman parte de la [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Debe tener el [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] instalado o la versión de [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] incluido en Visual Studio. Para obtener más información, vea [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=158044) en MSDN.  
  
- Proporcione una aplicación para implementar.  
  
     En este tutorial se da por supuesto que tiene una aplicación de Windows que está preparada para implementar. Esta aplicación se conoce como AppToDeploy.  
  
- Determine cómo se distribuirá la implementación.  
  
     Las opciones de distribución incluyen: Web, recurso compartido de archivos o CD. Para obtener más información, consulta [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
- Determine si la aplicación requiere un nivel elevado de confianza.  
  
     Si su aplicación requiere plena confianza (por ejemplo, acceso completo al sistema del usuario), puede usar la opción `-TrustLevel` de Mage. exe para establecer este valor. Si desea definir un conjunto de permisos personalizado para la aplicación, puede copiar la sección de permisos de Internet o de la intranet desde otro manifiesto, modificarla para adaptarla a sus necesidades y agregarla al manifiesto de aplicación mediante un editor de texto o MageUI. exe. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
- Obtener un certificado Authenticode.  
  
     Debe firmar la implementación con un certificado Authenticode. Puede generar un certificado de prueba mediante las herramientas de Visual Studio, MageUI. exe o MakeCert. exe y Pvk2Pfx. exe, o bien puede obtener un certificado de una entidad de certificación (CA). Si opta por utilizar una implementación de aplicación de confianza, también debe realizar una instalación única del certificado en todos los equipos cliente. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    > También puede firmar la implementación con un certificado CNG que puede obtener de una entidad de certificación.  
  
- Asegúrese de que la aplicación no tiene un manifiesto con información de UAC.  
  
     Debe determinar si la aplicación contiene un manifiesto con información de control de cuentas de usuario (UAC), como un elemento `<dependentAssembly>`. Para examinar un manifiesto de aplicación, puede usar la utilidad [Sigcheck](https://go.microsoft.com/fwlink/?LinkId=158035) de Windows Sysinternals.  
  
     Si la aplicación contiene un manifiesto con detalles de UAC, debe volver a compilarlo sin la información de UAC. Para un C# proyecto en Visual Studio, abra las propiedades del proyecto y seleccione la pestaña aplicación. En la lista desplegable **manifiesto** , seleccione **crear aplicación sin un manifiesto**. Para un proyecto de Visual Basic en Visual Studio, abra las propiedades del proyecto, seleccione la pestaña aplicación y haga clic en **Ver configuración de UAC**. En el archivo de manifiesto abierto, quite todos los elementos incluidos en el único elemento de `<asmv1:assembly>`.  
  
- Determine si la aplicación requiere requisitos previos en el equipo cliente.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicaciones implementadas desde Visual Studio pueden incluir un programa previo de instalación de requisitos previos (Setup. exe) con la implementación. En este tutorial se crean los dos manifiestos necesarios para una implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Puede crear un programa previo de requisitos previos mediante la [tarea GenerateBootstrapper (](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Para implementar una aplicación con la herramienta de línea de comandos Mage. exe  
  
1. Cree un directorio en el que almacenará los archivos de implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2. En el directorio de implementación que acaba de crear, cree un subdirectorio de versión. Si es la primera vez que implementa la aplicación, asigne el nombre **1.0.0.0**al subdirectorio de la versión.  
  
    > [!NOTE]
    > La versión de la implementación puede ser distinta de la versión de la aplicación.  
  
3. Copie todos los archivos de aplicación en el subdirectorio de la versión, incluidos los archivos ejecutables, los ensamblados, los recursos y los archivos de datos. Si es necesario, puede crear subdirectorios adicionales que contengan archivos adicionales.  
  
4. Abra el símbolo del sistema de [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] o Visual Studio y cambie al subdirectorio de la versión.  
  
5. Cree el manifiesto de aplicación con una llamada a Mage. exe. La siguiente instrucción crea un manifiesto de aplicación para el código compilado para ejecutarse en el procesador Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    > Asegúrese de incluir el punto (.) después de la opción `-FromDirectory`, que indica el directorio actual. Si no incluye el punto, debe especificar la ruta de acceso a los archivos de aplicación.  
  
6. Firme el manifiesto de aplicación con el certificado Authenticode. Reemplace *mycert. pfx* con la ruta de acceso al archivo de certificado. Reemplace *passwd* por la contraseña del archivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Para firmar el manifiesto de aplicación con un certificado CNG, use lo siguiente. Reemplace *cngCert. pfx* por la ruta de acceso al archivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7. Cambie a la raíz del directorio de implementación.  
  
8. Genere el manifiesto de implementación con una llamada a Mage. exe. De forma predeterminada, Mage. exe marcará la implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] como una aplicación instalada, de modo que se pueda ejecutar tanto en línea como sin conexión. Para que la aplicación esté disponible solo cuando el usuario está en línea, use la opción `-Install` con un valor de `false`. Si usa el valor predeterminado, y los usuarios instalarán la aplicación desde un sitio web o un recurso compartido de archivos, asegúrese de que el valor de la opción `-ProviderUrl` señale a la ubicación del manifiesto de aplicación en el servidor web o recurso compartido.  
  
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
  
10. Copie todos los archivos del directorio de implementación en el destino o el medio de implementación. Puede ser una carpeta de un sitio web o un sitio FTP, un recurso compartido de archivos o un CD-ROM.  
  
11. Proporcione a los usuarios la dirección URL, la UNC o el medio físico necesarios para instalar la aplicación. Si proporciona una dirección URL o una UNC, debe proporcionar a los usuarios la ruta de acceso completa al manifiesto de implementación. Por ejemplo, si AppToDeploy se implementa en http://webserver01/ en el directorio AppToDeploy, la ruta de acceso de dirección URL completa sería http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Para implementar una aplicación con la herramienta gráfica MageUI. exe  
  
1. Cree un directorio en el que almacenará los archivos de implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2. En el directorio de implementación que acaba de crear, cree un subdirectorio de versión. Si es la primera vez que implementa la aplicación, asigne el nombre **1.0.0.0**al subdirectorio de la versión.  
  
    > [!NOTE]
    > La versión de la implementación es probablemente distinta de la versión de la aplicación.  
  
3. Copie todos los archivos de aplicación en el subdirectorio de la versión, incluidos los archivos ejecutables, los ensamblados, los recursos y los archivos de datos. Si es necesario, puede crear subdirectorios adicionales que contengan archivos adicionales.  
  
4. Inicie la herramienta gráfica MageUI. exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5. Cree un nuevo manifiesto de aplicación seleccionando **archivo**, **nuevo**, **manifiesto de aplicación** en el menú.  
  
6. En la pestaña **nombre** predeterminado, escriba el nombre y el número de versión de esta implementación. Especifique también el **procesador** para el que se ha creado la aplicación, como x86.  
  
7. Seleccione la pestaña **archivos** y haga clic en el botón de puntos suspensivos ( **...** ) situado junto al cuadro de texto directorio de la **aplicación** . Aparece el cuadro de diálogo Buscar carpeta.  
  
8. Seleccione el subdirectorio de versión que contiene los archivos de aplicación y, a continuación, haga clic en **Aceptar**.  
  
9. Si va a realizar la implementación desde Internet Information Services (IIS), active la casilla **al rellenar agregar la extensión. deploy a cualquier archivo que no la tenga** .  
  
10. Haga clic en el botón **rellenar** para agregar todos los archivos de aplicación a la lista de archivos. Si la aplicación contiene más de un archivo ejecutable, marque el archivo ejecutable principal para esta implementación como aplicación de inicio; para ello, seleccione **punto de entrada** en la lista desplegable tipo de **archivo** . (Si la aplicación contiene un solo archivo ejecutable, MageUI. exe lo marcará automáticamente).  
  
11. Seleccione la pestaña **permisos necesarios** y seleccione el nivel de confianza que necesita para la aplicación. El valor predeterminado es **FullTrust**, que será adecuado para la mayoría de las aplicaciones.  
  
12. Seleccione **archivo**, **Guardar como** en el menú. Aparece un cuadro de diálogo Opciones de firma que le pide que firme el manifiesto de aplicación.  
  
13. Si tiene un certificado almacenado como un archivo en el sistema de archivos, use la opción **firmar con el archivo de certificado** y seleccione el certificado del sistema de archivos mediante el botón de puntos suspensivos ( **...** ). A continuación, escriba la contraseña del certificado.  
  
     O bien,  
  
     Si el certificado se mantiene en un almacén de certificados al que se puede tener acceso desde el equipo, seleccione la opción **firmar con certificado almacenado** y seleccione el certificado en la lista proporcionado.  
  
14. Haga clic en **Aceptar** para firmar el manifiesto de aplicación. Aparece el cuadro de diálogo Guardar como.  
  
15. En el cuadro de diálogo Guardar como, especifique el directorio de la versión y, a continuación, haga clic en **Guardar**.  
  
16. Seleccione **archivo**, **nuevo**, **manifiesto de implementación** en el menú para crear el manifiesto de implementación.  
  
17. En la pestaña **nombre** , especifique un nombre y un número de versión para esta implementación (**1.0.0.0** en este ejemplo). Especifique también el **procesador** para el que se ha creado la aplicación, como x86.  
  
18. Seleccione la pestaña **Descripción** y especifique los valores para el **publicador** y el **producto**. (**Product** es el nombre asignado a la aplicación en el menú Inicio de Windows cuando la aplicación se instala en un equipo cliente para su uso sin conexión).  
  
19. Seleccione la pestaña **Opciones de implementación** y, en el cuadro de texto ubicación de **Inicio** , especifique la ubicación del manifiesto de aplicación en el servidor web o el recurso compartido. Por ejemplo, \\\myServer\myShare\AppToDeploy.application.  
  
20. Si ha agregado la extensión. deploy en un paso anterior, seleccione usar también la **extensión de nombre de archivo. deploy** .  
  
21. Seleccione la pestaña **Opciones de actualización** y especifique la frecuencia con la que desea que se actualice la aplicación. Si su aplicación usa <xref:System.Deployment.Application.UpdateCheckInfo> para buscar actualizaciones, desactive la casilla **esta aplicación debe buscar actualizaciones** .  
  
22. Seleccione la pestaña **referencia de aplicación** y, a continuación, haga clic en el botón **seleccionar manifiesto** . Aparece un cuadro de diálogo Abrir.  
  
23. Seleccione el manifiesto de aplicación que creó anteriormente y, a continuación, haga clic en **abrir**.  
  
24. Seleccione **archivo**, **Guardar como** en el menú. Aparece un cuadro de diálogo Opciones de firma que le pide que firme el manifiesto de implementación.  
  
25. Si tiene un certificado almacenado como un archivo en el sistema de archivos, use la opción **firmar con el archivo de certificado** y seleccione el certificado del sistema de archivos mediante el botón de puntos suspensivos ( **...** ). A continuación, escriba la contraseña del certificado.  
  
     O bien,  
  
     Si el certificado se mantiene en un almacén de certificados al que se puede tener acceso desde el equipo, seleccione la opción **firmar con certificado almacenado** y seleccione el certificado en la lista proporcionado.  
  
26. Haga clic en **Aceptar** para firmar el manifiesto de implementación. Aparece el cuadro de diálogo Guardar como.  
  
27. En el cuadro de diálogo **Guardar como** , mueva un directorio hacia arriba en la raíz de la implementación y, a continuación, haga clic en **Guardar**.  
  
28. Copie todos los archivos del directorio de implementación en el destino o el medio de implementación. Puede ser una carpeta de un sitio web o un sitio FTP, un recurso compartido de archivos o un CD-ROM.  
  
29. Proporcione a los usuarios la dirección URL, la UNC o el medio físico necesarios para instalar la aplicación. Si proporciona una dirección URL o una UNC, debe proporcionar a los usuarios la ruta de acceso completa del manifiesto de implementación. Por ejemplo, si AppToDeploy se implementa en http://webserver01/ en el directorio AppToDeploy, la ruta de acceso de dirección URL completa sería http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Cuando necesite implementar una nueva versión de la aplicación, cree un nuevo directorio con el nombre de la nueva versión (por ejemplo, 1.0.0.1) y copie los nuevos archivos de aplicación en el nuevo directorio. A continuación, debe seguir los pasos anteriores para crear y firmar un nuevo manifiesto de aplicación y actualizar y firmar el manifiesto de implementación. Tenga cuidado de especificar la misma versión superior en las llamadas de Mage. exe `-New` y `–Update`, ya que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] solo actualiza las versiones superiores, con el entero más a la izquierda más significativo. Si ha usado MageUI. exe, puede actualizar el manifiesto de implementación; para ello, ábralo, seleccione la pestaña **referencia de aplicación** , haga clic en el botón **seleccionar manifiesto** y, a continuación, seleccione el manifiesto de aplicación actualizado.  
  
## <a name="see-also"></a>Vea también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)
