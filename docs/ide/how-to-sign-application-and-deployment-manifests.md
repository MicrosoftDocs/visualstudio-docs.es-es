---
title: "C&#243;mo: Firmar aplicaciones y manifiestos de implementaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "manifiestos de aplicación [Visual Studio]"
  - "ensamblados [Visual Studio], firmar"
  - "implementación ClickOnce [Visual Studio], firmar ensamblados"
  - "firma de código [Visual Studio], Authenticode"
  - "manifiestos de implementación [Visual Studio]"
  - "archivos clave [Visual Studio]"
  - "manifiestos [Visual Studio]"
  - "firmar manifiestos [Visual Studio]"
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
caps.latest.revision: 58
caps.handback.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Firmar aplicaciones y manifiestos de implementaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si desea publicar una aplicación mediante la implementación ClickOnce, los manifiestos de aplicación e implementación deben estar firmados con un par de claves privada y pública y mediante la tecnología Authenticode.  Puede firmar los manifiestos utilizando un certificado del almacén de certificados de Windows o un archivo de clave.  
  
 Para obtener más información sobre la implementación de ClickOnce, vea [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
 La firma de los manifiestos de ClickOnce es opcional para las aplicaciones basadas en .exe.  Para obtener más información, vea la sección "Generar un manifiesto sin firmar" de este documento.  
  
 Para obtener información sobre cómo crear los archivos de clave, consulte [Cómo: Crear un par de claves privada y pública](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md).  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] admite únicamente archivos de clave de intercambio de información personal \(PFX\) que tengan la extensión .pfx.  Sin embargo, puede seleccionar otros tipos de certificados del almacén de certificados de Windows del usuario actual haciendo clic en **Seleccionar del almacén** en la página **Firma** de propiedades de proyecto.  
  
### Para firmar los manifiestos de aplicación y de implementación mediante un certificado  
  
1.  Vaya a la ventana de propiedades del proyecto \(haga clic con el botón secundario en el proyecto en **Explorador de soluciones** y seleccione **Propiedades**, o escriba propiedades del proyecto en la ventana de **Inicio rápido**, o presione ALT\+INTRO en la ventana de **Explorador de soluciones**\).  En la pestaña **Firma**, active la casilla **Firmar los manifiestos de ClickOnce**.  
  
2.  Haga clic en el botón **Seleccionar del almacén**.  
  
     El cuadro de diálogo **Seleccionar un certificado** aparece y muestra el contenido del almacén de certificados de Windows.  
  
    > [!TIP]
    >  Si hace clic en **Haga clic aquí para ver las propiedades del certificado**, el cuadro de diálogo **Detalles del certificado** aparece.  Este cuadro de diálogo incluye información detallada sobre el certificado e incluye opciones adicionales.  Puede hacer clic en **certificados** para ver información adicional de ayuda.  
  
3.  Seleccione el certificado que desea utilizar para firmar los manifiestos.  
  
4.  Asimismo, puede especificar la dirección de un servidor de marca de tiempo en el cuadro de texto **Dirección URL del servidor de marca de tiempo**.  Es un servidor que proporciona una marca de tiempo que especifica cuando se firmó el manifiesto.  
  
### Para firmar manifiestos de aplicación y de implementación mediante un archivo de clave existente  
  
1.  En la página **Firma**, active la casilla **Firmar los manifiestos de ClickOnce**.  
  
2.  Haga clic en el botón **Seleccionar del archivo**.  
  
     Aparecerá el cuadro de diálogo **Seleccionar archivo**.  
  
3.  Cuando aparezca el cuadro de diálogo **Seleccionar archivo**, desplácese a la ubicación del archivo de clave \(.pfx\) que desee utilizar y haga clic en **Abrir**.  
  
    > [!NOTE]
    >  Esta opción sólo admite archivos que tengan la extensión .pfx.  Si tiene un archivo de clave o un certificado en otro formato, almacénelo en el almacén de certificados de Windows y seleccione el certificado como se describe en el procedimiento anterior.  El propósito del certificado seleccionado debería incluir la firma de código.  
  
     El cuadro de diálogo de **Escribir la contraseña para abrir el archivo** aparece. \(Si el archivo .pfx ya está almacenado en el almacén de certificados de Windows, o no está protegido por contraseña, no se le pedirá que escriba una contraseña.\)  
  
4.  Escriba la contraseña para tener acceso al archivo de clave y presione ENTRAR.  
  
### Para firmar los manifiestos de aplicación y de implementación mediante un certificado de prueba  
  
1.  En la página **Firma**, active la casilla **Firmar los manifiestos de ClickOnce**.  
  
2.  Para crear un nuevo certificado con fines de pruebas, haga clic en el botón **Crear certificado de prueba**.  
  
3.  En el cuadro de diálogo de **Crear certificado de prueba**, escriba una contraseña para ayudar a proteger el certificado de prueba.  
  
## Generar un manifiesto sin firmar  
 La firma de los manifiestos de ClickOnce es opcional para las aplicaciones basadas en .exe.  Los procedimientos siguientes muestran cómo generar manifiestos sin firmar de ClickOnce.  
  
> [!IMPORTANT]
>  Los manifiestos sin firmar pueden simplificar el desarrollo y las pruebas de la aplicación.  Sin embargo, los manifiestos sin firmar son una oportunidad de riesgos para la seguridad sustanciales en un entorno de producción.  Considere el uso de manifiestos sin firmar únicamente si la aplicación de ClickOnce se ejecuta en equipos dentro de una intranet que está completamente aislada de Internet y otros orígenes de código malintencionado.  
  
 De forma predeterminada, ClickOnce genera automáticamente manifiestos firmados a menos que se excluyan de forma específica uno o varios archivos del código hash generado.  Es decir, con la publicación de la aplicación se generan manifiestos firmados si todos los archivos se incluyen en el código hash, aun cuando la casilla **Firmar los manifiestos de ClickOnce** esté desactivada.  
  
#### Para generar manifiestos sin firmar e incluir todos los archivos en el código hash generado  
  
1.  Para generar manifiestos sin firmar que incluyan todos los archivos en el código hash, debe publicar primero la aplicación junto con los manifiestos firmados.  Por consiguiente, firme primero los manifiestos de ClickOnce siguiendo uno de los procedimientos anteriores y, a continuación, publique la aplicación.  
  
2.  En la página **Firma**, desactive la casilla **Firmar los manifiestos de ClickOnce**.  
  
3.  Restablezca la versión de publicación de forma que solo haya disponible una versión de la aplicación.  De manera predeterminada, Visual Studio incrementa automáticamente el número de revisión de la versión de publicación cada vez que se publica una aplicación.  Para obtener más información, vea [Cómo: Establecer la versión de publicación de ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md).  
  
4.  Publique la aplicación  
  
#### Para generar manifiestos sin firmar y excluir uno o más archivos del código hash generado  
  
1.  En la página **Firma**, desactive la casilla **Firmar los manifiestos de ClickOnce**.  
  
2.  Abra el cuadro de diálogo **Archivos de aplicación** y establezca **Hash** en **Excluir** para los archivos que desea excluir del código hash generado.  
  
    > [!NOTE]
    >  Al excluir un archivo del código hash se configura ClickOnce para deshabilitar la firma automática de los manifiestos, por lo que no es necesario publicar primero con los manifiestos firmados como se muestra en el procedimiento anterior.  
  
3.  Publique la aplicación  
  
## Vea también  
 [Ensamblados con nombre seguro](../Topic/Strong-Named%20Assemblies.md)   
 [Cómo: Crear un par de claves privada y pública](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md)   
 [Página Firma, Diseñador de proyectos](../ide/reference/signing-page-project-designer.md)   
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)