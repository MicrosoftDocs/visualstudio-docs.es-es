---
title: "Tutorial: Implementar manualmente una aplicaci&#243;n ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, manualmente"
  - "implementación ClickOnce, herramientas de SDK"
  - "implementar aplicaciones [ClickOnce], implementaciones manuales de ClickOnce"
  - "Mage.exe, implementaciones manuales de ClickOnce"
  - "MageUI.exe, implementaciones manuales de ClickOnce"
  - "manifiestos [ClickOnce]"
  - "implementaciones manuales de ClickOnce"
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 49
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tutorial: Implementar manualmente una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si no puede usar Visual Studio para implementar la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o necesita usar características avanzadas de implementación, como la implementación de aplicaciones de confianza, debería usar la herramienta de línea de comandos Mage.exe para crear los manifiestos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  En este tutorial se describe cómo crear una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante la versión de línea de comandos \(Mage.exe\) o la versión gráfica \(MageUI.exe\) de la herramienta de generación y edición de manifiestos.  
  
## Requisitos previos  
 En este tutorial existen algunas opciones y requisitos previos que se deben elegir antes de compilar una implementación.  
  
-   Instale Mage.exe y MageUI.exe.  
  
     Mage.exe y MageUI.exe forman parte del [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Debe tener instalado el [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] o la versión del [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] incluida con Visual Studio.  Para obtener más información, vea [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) en MSDN.  
  
-   Proporcione una aplicación para implementar.  
  
     En este tutorial se da por supuesto que tiene una aplicación Windows lista para implementar.  Se hará referencia a esta aplicación como AppToDeploy.  
  
-   Determine cómo se distribuirá la implementación.  
  
     Entre las opciones de distribución se incluyen la Web, un recurso compartido de archivos o un CD.  Para obtener más información, vea [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
-   Determine si la aplicación requiere un nivel de confianza elevado.  
  
     Si la aplicación requiere Plena confianza, por ejemplo, acceso total al sistema del usuario, puede usar la opción `-TrustLevel` de Mage.exe para establecerlo.  Si desea definir un conjunto de permisos personalizados para la aplicación, puede copiar la sección de permisos de Internet o Intranet de otro manifiesto, modificarlo para ajustarlo a sus necesidades y agregarlo al manifiesto de la aplicación utilizando un editor de texto o MageUI.exe.  Para obtener más información, vea [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
-   Obtenga un certificado Authenticode.  
  
     Debería firmar la implementación con un certificado Authenticode.  Puede generar un certificado de prueba mediante las herramientas Visual Studio, MageUI.exe o MakeCert.exe y Pvk2Pfx.exe o bien obtener un certificado de una entidad de certificación \(CA\).  Si decide utilizar la implementación de aplicaciones de confianza, también tendrá que realizar una instalación única del certificado en todos los equipos cliente.  Para obtener más información, vea [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
-   Asegúrese de que la aplicación no tiene un manifiesto con información de UAC.  
  
     Es necesario determinar si la aplicación contiene un manifiesto con información de Control de cuentas de usuario \(UAC\), como un elemento `<dependentAssembly>`.  Para examinar un manifiesto de aplicación, puede usar la utilidad de Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035).  
  
     Si la aplicación contiene un manifiesto con detalles de UAC, deberá volver a compilarla sin dicha información.  Para un proyecto de C\# en Visual Studio, abra las propiedades del proyecto y seleccione la pestaña Aplicación.  En la lista desplegable **Manifiesto**, seleccione **Crear aplicación sin manifiesto**.  Para un proyecto de Visual Basic en Visual Studio, abra las propiedades del proyecto, seleccione la pestaña Aplicación y haga clic en **Ver configuración de UAC**.  En el archivo de manifiesto abierto, quite todos los elementos incluidos en el elemento `<asmv1:assembly>` único.  
  
-   Determine si la aplicación requiere determinados requisitos previos en el equipo cliente.  
  
     Las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementadas desde Visual Studio pueden incluir un arranque de instalación de requisitos previos \(setup.exe\) con la implementación.  En este tutorial se crean los dos manifiestos requeridos para una implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Puede crear un arranque de requisitos previos mediante [GenerateBootstrapper \(Tarea\)](../msbuild/generatebootstrapper-task.md).  
  
### Para implementar una aplicación con la herramienta de línea de comandos Mage.exe  
  
1.  Cree un directorio donde se almacenarán los archivos de implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  En el directorio de implementación que acaba de crear, cree un subdirectorio de la versión.  Si esta es la primera vez que implementa la aplicación, asigne el nombre 1.0.0.0 al subdirectorio de la versión.  
  
    > [!NOTE]
    >  La versión de la implementación puede ser distinta de la versión de la aplicación.  
  
3.  Copie todos los archivos de la aplicación en el subdirectorio de la versión, incluidos los archivos ejecutables, ensamblados, recursos y archivos de datos.  Si es necesario, puede crear otros subdirectorios que incluyan los archivos adicionales.  
  
4.  Abra el símbolo del sistema de Visual Studio o [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] y cambie al subdirectorio de la versión.  
  
5.  Cree el manifiesto de aplicación con una llamada a Mage.exe.  En la instrucción siguiente se crea un manifiesto de aplicación para el código compilado para ejecutarse en el procesador Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Asegúrese de incluir el punto \(.\) después de la opción `-FromDirectory`, que especifica el directorio actual.  Si no se incluye el punto, debe especificarse la ruta de acceso a los archivos de la aplicación.  
  
6.  Firme el manifiesto de aplicación con el certificado Authenticode.  Reemplace *mycert.pfx* con la ruta de acceso al archivo de certificado.  Reemplace *passwd* con la contraseña para el archivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
7.  Cambie a la raíz del directorio de implementación.  
  
8.  Genere el manifiesto de implementación con una llamada a Mage.exe.  De forma predeterminada, Mage.exe marcará la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] como una aplicación instalada para que se pueda ejecutar tanto en línea como sin conexión.  Para establecer que la aplicación esté disponible solo cuando el usuario está en línea, use la opción `-Install` con el valor `false`.  Si se usa el valor predeterminado, y los usuarios instalan la aplicación desde un sitio web o un recurso compartido de archivos, asegúrese de que el valor de la opción `-ProviderUrl` apunta a la ubicación del manifiesto de aplicación en el servidor web o el recurso compartido.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Firme el manifiesto de implementación con el certificado Authenticode.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. Copie todos los archivos del directorio de implementación en los medios o el destino de implementación.  Puede ser una carpeta en un sitio web o sitio FTP, un recurso compartido de archivos o un CD\-ROM.  
  
11. Proporcione a los usuarios la dirección URL, UNC o los medios de comunicación físicos necesarios para instalar la aplicación.  Si proporciona una dirección URL o una UNC, debe ofrecer a los usuarios la ruta de acceso completa al manifiesto de implementación.  Por ejemplo, si AppToDeploy se implementa en http:\/\/webserver01\/ en el directorio AppToDeploy, la ruta de acceso completa de la dirección URL sería http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
### Para implementar una aplicación con la herramienta gráfica MageUI.exe  
  
1.  Cree un directorio donde se almacenarán los archivos de implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  En el directorio de implementación que acaba de crear, cree un subdirectorio de la versión.  Si esta es la primera vez que implementa la aplicación, asigne el nombre 1.0.0.0 al subdirectorio de la versión.  
  
    > [!NOTE]
    >  La versión de la implementación probablemente es distinta de la versión de la aplicación.  
  
3.  Copie todos los archivos de la aplicación en el subdirectorio de la versión, incluidos los archivos ejecutables, ensamblados, recursos y archivos de datos.  Si es necesario, puede crear otros subdirectorios que incluyan los archivos adicionales.  
  
4.  Inicie la herramienta gráfica MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Cree un nuevo manifiesto de aplicación seleccionando **Archivo**, **Nuevo**, **Manifiesto de la aplicación** en el menú.  
  
6.  En la pestaña **Nombre** predeterminada, escriba el nombre y el número de versión de esta implementación.  Especifique también el **Procesador** para el que se ha compilado su aplicación, por ejemplo x86.  
  
7.  Seleccione la pestaña **Archivos** y haga clic en el botón de puntos suspensivos \(**...**\) situado junto al cuadro de texto **Directorio de aplicación**.  Aparece el cuadro de diálogo Buscar carpeta.  
  
8.  Seleccione el subdirectorio de la versión que contiene los archivos de su aplicación y, a continuación, haga clic en **Aceptar**.  
  
9. Si va a realizar la implementación desde Internet Information Services \(IIS\), active la casilla **Al rellenar, agregar la extensión .deploy a los archivos que no la tengan**.  
  
10. Haga clic en el botón **Rellenar** para agregar todos sus archivos de aplicación a la lista de archivos.  Si la aplicación contiene más de un archivo ejecutable, marque el archivo ejecutable principal de esta implementación como la aplicación de inicio seleccionando **Punto de entrada** en la lista desplegable **Tipo de archivo**.  \(Si solo contiene un archivo ejecutable, MageUI.exe lo marcará para usted\).  
  
11. Seleccione la pestaña **Permisos necesarios** y seleccione el nivel de confianza que la aplicación necesita afirmar.  El valor predeterminado es **FullTrust**, adecuado para la mayoría de las aplicaciones.  
  
12. Seleccione **Archivo**, **Guardar como** en el menú.  Aparece el cuadro de diálogo Opciones de firma, donde se solicita que firme el manifiesto de aplicación.  
  
13. Si tiene un certificado almacenado como archivo en el sistema de archivos, use la opción **Firmar con archivo de certificado** y seleccione el certificado en el sistema de archivos mediante el botón de puntos suspensivos \(**...**\).  A continuación, escriba la contraseña del certificado.  
  
     O bien  
  
     Si el certificado se guarda en un almacén de certificados al que se puede obtener acceso desde el equipo, seleccione la opción **Firmar con certificado almacenado** y luego seleccione el certificado en la lista suministrada.  
  
14. Haga clic en **Aceptar** para firmar el manifiesto de aplicación.  Aparece el cuadro de diálogo Guardar como.  
  
15. En el cuadro de diálogo Guardar como, especifique el directorio de la versión y, a continuación, haga clic en **Guardar**.  
  
16. Seleccione en el menú las opciones **Archivo**, **Nuevo** y **Manifiesto de implementación** para crear un manifiesto de implementación.  
  
17. En la pestaña **Nombre**, especifique un nombre y un número de versión para esta implementación \(en este ejemplo, 1.0.0.0\).  Especifique también el **Procesador** para el que se ha compilado su aplicación, por ejemplo x86.  
  
18. Seleccione la pestaña **Descripción** y especifique los valores de **Publicador** y **Producto**.  \(**Producto** es el nombre que se asigna a la aplicación en el menú Inicio de Windows cuando esta se instala en un equipo cliente para su uso sin conexión\).  
  
19. Seleccione la pestaña **Opciones de implementación** y especifique la ubicación del manifiesto de aplicación en el servidor web o el recurso compartido en el cuadro de texto **Ubicación de inicio**.  Por ejemplo, \\\\myServer\\myShare\\AppToDeploy.application.  
  
20. Si ya se ha agregado la extensión .deploy en un paso anterior, seleccione también aquí **Usar la extensión de nombre de archivo .deploy**.  
  
21. Seleccione la pestaña **Opciones de actualización** y especifique la frecuencia con la que desea que se actualice esta aplicación.  Si la aplicación usa <xref:System.Deployment.Application.UpdateCheckInfo> para comprobar las actualizaciones, desactive la casilla **Esta aplicación debe buscar actualizaciones**.  
  
22. Seleccione la pestaña **Referencia de aplicación** y, a continuación, haga clic en el botón **Seleccionar manifiesto**.  Se abre un cuadro de diálogo.  
  
23. Seleccione el manifiesto de aplicación que ha creado anteriormente y, a continuación, haga clic en **Abrir**.  
  
24. Seleccione **Archivo**, **Guardar como** en el menú.  Aparece el cuadro de diálogo Opciones de firma, donde se solicita que firme el manifiesto de implementación.  
  
25. Si tiene un certificado almacenado como archivo en el sistema de archivos, use la opción **Firmar con archivo de certificado** y seleccione el certificado en el sistema de archivos mediante el botón de puntos suspensivos \(**...**\).  A continuación, escriba la contraseña del certificado.  
  
     O bien  
  
     Si el certificado se guarda en un almacén de certificados al que se puede obtener acceso desde el equipo, seleccione la opción **Firmar con certificado almacenado** y luego seleccione el certificado en la lista suministrada.  
  
26. Haga clic en **Aceptar** para firmar el manifiesto de implementación.  Aparece el cuadro de diálogo Guardar como.  
  
27. En el cuadro de diálogo **Guardar como**, suba un directorio hacia la raíz de la implementación y, a continuación, haga clic en **Guardar**.  
  
28. Copie todos los archivos del directorio de implementación en los medios o el destino de implementación.  Puede ser una carpeta en un sitio web o sitio FTP, un recurso compartido de archivos o un CD\-ROM.  
  
29. Proporcione a los usuarios la dirección URL, UNC o los medios de comunicación físicos necesarios para instalar la aplicación.  Si proporciona una dirección URL o una UNC, debe ofrecer a los usuarios la ruta de acceso completa al manifiesto de implementación.  Por ejemplo, si AppToDeploy se implementa en http:\/\/webserver01\/ en el directorio AppToDeploy, la ruta de acceso completa de la dirección URL sería http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
## Pasos siguientes  
 Cuando necesite implementar una nueva versión de la aplicación, cree un nuevo directorio con el nombre de la nueva versión, por ejemplo, 1.0.0.1, y copie los nuevos archivos de aplicación en dicho directorio.  A continuación, debe seguir los pasos anteriores para crear y firmar un nuevo manifiesto de aplicación, además de actualizar y firmar el manifiesto de implementación.  Es importante especificar la misma versión superior en las llamadas `-New` y `–Update` de Mage.exe, ya que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] solamente actualiza las versiones superiores, donde el entero situado a la izquierda es el más significativo.  Si se ha usado MageUI.exe y desea actualizar el manifiesto de implementación, ábralo, seleccione la pestaña **Referencia de aplicación**, haga clic en el botón **Seleccionar manifiesto** y, a continuación, seleccione el manifiesto de aplicación actualizado.  
  
## Vea también  
 [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)