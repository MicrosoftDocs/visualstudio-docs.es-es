---
title: 'Tutorial: Implementar manualmente una aplicación ClickOnce que no requiere volver a firmar y que conserve la información de personalización de marca | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91f552ce30030abeae6af0d63763625e711d32e2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875104"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Tutorial: Implementar manualmente una aplicación ClickOnce que no requiere volver a firmar y que conserve la información de personalización de marca
Cuando creas un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación y, a continuación, asígnele a un cliente para publicar e implementar, el cliente había tradicionalmente actualizar el manifiesto de implementación y volver a firmarlo. Si bien esto sigue siendo el método preferido en la mayoría de los casos, .NET Framework 3.5 le permite crear [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las implementaciones que los clientes pueden implementar sin tener que volver a generar un nuevo manifiesto de implementación. Para obtener más información, consulte [ClickOnce implementar aplicaciones para servidores de pruebas y producción sin nueva firma](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).  
  
 Cuando creas un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación y, a continuación, asígnele a un cliente para publicar e implementar, la aplicación puede usar la personalización de marca del cliente o puede conservar su marca. Por ejemplo, si la aplicación es una única aplicación propia, es posible que desea conservar la personalización de marca. Si la aplicación está muy personalizada para cada cliente, puede usar la personalización de marca del cliente. .NET Framework 3.5 le permite conservar la personalización de marca, información del publicador y firma de seguridad al proporcionar a una aplicación a una organización para la implementación. Para obtener más información, consulte [ClickOnce crear aplicaciones para que otros usuarios implementar](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  En este tutorial crea implementaciones manualmente mediante la herramienta de línea de comandos *Mage.exe* o la herramienta gráfica *MageUI.exe*. Para obtener más información acerca de las implementaciones manuales, vea [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para llevar a cabo los pasos de este tutorial necesita lo siguiente:  
  
-   Una aplicación de Windows Forms que esté listo para implementar. Se hará referencia a esta aplicación como *WindowsFormsApp1*.  
  
-   Visual Studio o el SDK de Windows.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Para implementar una aplicación ClickOnce con diferentes implementaciones y personalización de marca de soporte técnico mediante Mage.exe  
  
1. Abra un símbolo del sistema de Visual Studio o un [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] símbolo del sistema y cambie al directorio en el que almacenará la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos.  
  
2. Cree un directorio con el nombre de la versión actual de la implementación. Si se trata de la primera vez que va a implementar la aplicación, probablemente elegirá **1.0.0.0**.  
  
   > [!NOTE]
   >  La versión de la implementación puede ser distinta de la versión de los archivos de aplicación.  
  
3. Cree un subdirectorio denominado **bin** y copie todos los archivos de aplicación aquí, incluidos los archivos ejecutables, ensamblados, recursos y archivos de datos.  
  
4. Generar el manifiesto de aplicación con una llamada a Mage.exe.  
  
   ```cmd  
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
   ```  
  
5. Inicie sesión en el manifiesto de aplicación con su certificado digital.  
  
   ```cmd  
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
   ```  
  
6. Generar el manifiesto de implementación con una llamada a *Mage.exe*. De forma predeterminada, *Mage.exe* marcará la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación como una aplicación instalada, por lo que TI puede ejecutarse tanto en línea y sin conexión. Para que la aplicación esté disponible solo cuando el usuario está conectado, use la `-i` argumento con un valor de `f`. Puesto que esta aplicación sacarán provecho de la característica de implementación de varios, excluir la `-providerUrl` argumento *Mage.exe*. (En las versiones de .NET Framework anteriores a la versión 3.5, excepto `-providerUrl` para una aplicación sin conexión, se producirá un error.)  
  
   ```cmd  
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
   ```  
  
7. No firma el manifiesto de implementación.  
  
8. Proporcione todos los archivos al cliente, que se implementará la aplicación en su red.  
  
9. En este momento, el cliente debe firmar el manifiesto de implementación con su propio certificado generado automáticamente. Por ejemplo, si el cliente trabaja para una compañía llamada Adventure Works, puede generar un certificado autofirmado mediante la *MakeCert.exe* herramienta. A continuación, use el *Pvk2pfx.exe* herramienta para combinar los archivos creados por *MakeCert.exe* en un archivo PFX que se puede pasar a *Mage.exe*.  
  
    ```cmd  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. A continuación, el cliente usa este certificado para firmar el manifiesto de implementación.  
  
    ```cmd  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. El cliente implementa la aplicación a sus usuarios.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Para implementar una aplicación ClickOnce con diferentes implementaciones y soporte técnico de personalización de marca mediante MageUI.exe  
  
1. Abra un símbolo del sistema de Visual Studio o un [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] símbolo del sistema y navegue hasta el directorio en el que almacenará la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] archivos.  
  
2. Cree un subdirectorio denominado **bin** y copie todos los archivos de aplicación aquí, incluidos los archivos ejecutables, ensamblados, recursos y archivos de datos.  
  
3. Cree un subdirectorio con el nombre de la versión actual de la implementación. Si se trata de la primera vez que va a implementar la aplicación, probablemente elegirá **1.0.0.0**.  
  
   > [!NOTE]
   >  La versión de la implementación puede ser distinta de la versión de los archivos de aplicación.  
  
4. Mover el \\ **bin** directorio en el directorio que creó en el paso 2.  
  
5. Inicie la herramienta gráfica *MageUI.exe*.  
  
   ```cmd  
   MageUI.exe  
   ```  
  
6. Crear un nuevo manifiesto de aplicación seleccionando **archivo**, **New**, **Application Manifest** en el menú.  
  
7. En el valor predeterminado **nombre** , escriba el nombre y número de versión de esta implementación. Además, proporcione un valor para **Publisher**, que se usará como el nombre de carpeta para el vínculo de acceso directo de la aplicación en el menú Inicio cuando se implementa.  
  
8. Seleccione el **opciones de la aplicación** ficha y haga clic en **manifiesto de aplicación de uso para la información de confianza**. Esto permitirá que la personalización de marca de terceros para este [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
9. Seleccione el **archivos** ficha y haga clic en el **examinar** situado junto a la **directorio de la aplicación** cuadro de texto.  
  
10. Seleccione el directorio que contiene los archivos de aplicación que creó en el paso 2 y haga clic en **Aceptar** en el cuadro de diálogo de selección de carpeta.  
  
11. Haga clic en el **rellenar** botón para agregar todos los archivos de aplicación a la lista de archivos. Si la aplicación contiene más de un archivo ejecutable, marque el archivo ejecutable principal de esta implementación como la aplicación de inicio seleccionando **punto de entrada** desde el **tipo de archivo** lista desplegable. (Si la aplicación solo contiene un archivo ejecutable, *MageUI.exe* marcará automáticamente.)  
  
12. Seleccione el **permisos necesarios** pestaña y seleccione el nivel de confianza que necesita la aplicación para la aserción. El valor predeterminado es **plena confianza**, que serán adecuados para la mayoría de las aplicaciones.  
  
13. Seleccione **archivo**, **guardar** en el menú y guarde el manifiesto de aplicación. Se le pedirá que firme el manifiesto de aplicación cuando la guarde.  
  
14. Si tiene un certificado almacenado como un archivo en el sistema de archivos, use el **inicio de sesión como archivo de certificado** opción y seleccione el certificado en el sistema de archivos mediante el botón de puntos suspensivos (**...** ) botón.  
  
     O bien  
  
     Si el certificado se guarda en un almacén de certificados que se puede acceder desde su equipo, seleccione el **opción firmar con certificado almacenado**y seleccione el certificado de la lista proporcionada.  
  
15. Seleccione **archivo**, **New**, **del manifiesto de implementación** en el menú para crear el manifiesto de implementación y, a continuación, en el **nombre** pestaña, proporcione un nombre y número de versión (**1.0.0.0** en este ejemplo).  
  
16. Cambie a la **actualizar** pestaña y especifique la frecuencia con que desea que esta aplicación para actualizar. Si la aplicación utiliza el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API de implementación para comprobar las actualizaciones, desactive la casilla de verificación **esta aplicación debe buscar actualizaciones**.  
  
17. Cambie a la **referencia de la aplicación** ficha. Puede rellenar previamente todos los valores de esta pestaña, haga clic en el **Seleccionar manifiesto** botón y seleccionando el manifiesto de aplicación que creó en pasos anteriores.  
  
18. Elija **guardar** y guarde el manifiesto de implementación en el disco. Se le pedirá que firme el manifiesto de aplicación cuando la guarde. Haga clic en **cancelar** para guardar el manifiesto sin firmar.  
  
19. Proporcione todos los archivos de aplicación al cliente.  
  
20. En este momento, el cliente debe firmar el manifiesto de implementación con su propio certificado generado automáticamente. Por ejemplo, si el cliente trabaja para una compañía llamada Adventure Works, puede generar un certificado autofirmado mediante la *MakeCert.exe* herramienta. A continuación, use el *Pvk2pfx.exe* herramienta para combinar los archivos creados por *MakeCert.exe* en un archivo PFX que se puede pasar a *MageUI.exe*.  
  
    ```cmd  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Con el certificado generado, el cliente puede firmar el manifiesto de implementación abriendo el manifiesto de implementación en *MageUI.exe*y luego guardarlo. Cuando aparezca el cuadro de diálogo firma, el cliente selecciona **inicio de sesión como archivo de certificado** opción y elegir el archivo PFX que guardó en disco.  
  
22. El cliente implementa la aplicación a sus usuarios.  
  
## <a name="see-also"></a>Vea también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert](/windows/desktop/SecCrypto/makecert)