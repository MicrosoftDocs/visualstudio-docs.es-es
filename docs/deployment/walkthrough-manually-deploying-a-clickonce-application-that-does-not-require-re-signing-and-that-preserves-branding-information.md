---
title: "Tutorial: Implementar manualmente una aplicaci&#243;n ClickOnce que no requiera el proceso de volver a firmar y que conserve la informaci&#243;n de marca comercial | Microsoft Docs"
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
  - "personalización de marca"
  - "aplicaciones ClickOnce, implementado por otros"
  - "implementación ClickOnce, manualmente"
  - "implementación ClickOnce, herramientas de SDK"
  - "implementaciones de cliente"
  - "manifiestos [ClickOnce]"
  - "implementaciones manuales de ClickOnce"
  - "marca comercial e implementaciones múltiples de ClickOnce"
  - "información de marca comercial conservada"
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tutorial: Implementar manualmente una aplicaci&#243;n ClickOnce que no requiera el proceso de volver a firmar y que conserve la informaci&#243;n de marca comercial
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando crea una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y, a continuación, se la proporciona a un cliente para que la publique e implemente, tradicionalmente el cliente tenía que actualizar el manifiesto de implementación y volver a firmarlo. Aunque este sigue siendo el método más recomendable en la mayoría de los casos, .NET Framework 3.5 permite crear implementaciones de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que los clientes pueden implementar sin tener que volver a generar un nuevo manifiesto de implementación.  Para obtener más información, consulte [Implementar aplicaciones ClickOnce para los servidores de pruebas y producción sin nueva firma](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Cuando crea una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y, a continuación, se la da a un cliente para que la publique e implemente, la aplicación puede utilizar la marca comercial del cliente o conservar la suya propia.  Por ejemplo, si se trata de una única aplicación propia, es posible que desee mantener su marca comercial.  Si la aplicación, por el contrario, está muy personalizada para cada cliente, quizás desee utilizar la marca comercial del cliente.  .NET Framework 3.5 le permite conservar su marca comercial, la información del editor y la firma de seguridad cuando proporciona una aplicación a una organización para que la implemente.  Para obtener más información, consulte [Crear aplicaciones ClickOnce para que las implementen terceros](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  En este tutorial creará manualmente las implementaciones utilizando la herramienta de línea de comandos Mage.exe o la herramienta gráfica MageUI.exe.  Para obtener más información sobre las implementaciones manuales, vea [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Requisitos previos  
 Para seguir los pasos de este tutorial, necesitará lo siguiente:  
  
-   Una aplicación de Windows Forms que esté lista para su implementación.  Esta aplicación la denominaremos WindowsFormsApp1.  
  
-   Visual Studio o SDK de Windows.  
  
### Para implementar una aplicación ClickOnce que sea compatible con diferentes implementaciones y marcas comerciales mediante Mage.exe  
  
1.  Abra un símbolo del sistema de Visual Studio o del [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] y cambie al directorio donde va a guardar los archivos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Cree un directorio con el nombre de la versión actual de la implementación.  Si esta es la primera vez que implementa la aplicación, es probable que elija 1.0.0.0.  
  
    > [!NOTE]
    >  La versión de la implementación puede ser distinta de la versión de los archivos de aplicación.  
  
3.  Cree un subdirectorio denominado bin y copie allí todos los archivos de la aplicación, incluidos los archivos ejecutables, ensamblados, recursos y archivos de datos.  
  
4.  Genere el manifiesto de aplicación con una llamada a Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Firme el manifiesto de aplicación con el certificado digital.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Genere el manifiesto de implementación con una llamada a Mage.exe.  De forma predeterminada, Mage.exe marcará la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] como una aplicación instalada para que se pueda ejecutar tanto en línea como sin conexión.  Para hacer que la aplicación esté disponible solo cuando el usuario esté en línea, utilice el argumento `-i` con el valor `f`.  Como esta aplicación aprovechará las ventajas de la característica de utilizar varias implementaciones, excluya el argumento `-providerUrl` en Mage.exe.  \(En las versiones de .NET Framework anteriores a la versión 3.5, si se excluyera el argumento `-providerUrl` de una aplicación sin conexión, se produciría un error\).  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  No firme el manifiesto de implementación.  
  
8.  Proporcione todos los archivos al cliente, que implementará la aplicación en su red.  
  
9. En este punto, el cliente debe firmar el manifiesto de implementación con su propio certificado.  Por ejemplo, si el cliente trabaja para una compañía llamada Adventure Works, puede generar un certificado autofirmado mediante la herramienta MakeCert.exe.  A continuación, utilizará la herramienta Pvk2pfx.exe para combinar los archivos creados por MakeCert.exe en un archivo PFX que se puede pasar a Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. El cliente utilizará después este certificado para firmar el manifiesto de implementación.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. El cliente implementa la aplicación para sus usuarios.  
  
### Para implementar una aplicación ClickOnce que sea compatible con diferentes implementaciones y marcas comerciales mediante MageUI.exe  
  
1.  Abra un símbolo del sistema de Visual Studio o del [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] y navegue al directorio donde va a guardar los archivos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Cree un subdirectorio denominado bin y copie allí todos los archivos de la aplicación, incluidos los archivos ejecutables, ensamblados, recursos y archivos de datos.  
  
3.  Cree un subdirectorio con el nombre de la versión actual de la implementación.  Si esta es la primera vez que implementa la aplicación, es probable que elija 1.0.0.0.  
  
    > [!NOTE]
    >  La versión de la implementación puede ser distinta de la versión de los archivos de aplicación.  
  
4.  Mueva el directorio \\bin al directorio que creó en el paso 2.  
  
5.  Inicie la herramienta gráfica MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Cree un nuevo manifiesto de aplicación seleccionando **Archivo**, **Nuevo**, **Manifiesto de la aplicación** en el menú.  
  
7.  En la ficha **Nombre** predeterminada, escriba el nombre y el número de versión de esta implementación.  Proporcione también un valor para **Publicador**, que se utilizará como nombre de carpeta en el vínculo de acceso directo de la aplicación del menú Inicio cuando se implemente.  
  
8.  Seleccione la ficha **Opciones de la aplicación** y haga clic en **Usar manifiesto de la aplicación para la información de confianza**.  De este modo, permitirá que terceras personas personalicen la marca comercial de esta aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
9. Seleccione la ficha **Archivos** y haga clic en el botón **Examinar** situado junto al cuadro de texto Directorio de aplicación.  
  
10. Seleccione el directorio que contiene los archivos de aplicación que creó en el paso 2 y haga clic en **Aceptar** en el cuadro de diálogo de selección de la carpeta.  
  
11. Haga clic en el botón **Rellenar** para agregar todos sus archivos de aplicación a la lista de archivos.  Si la aplicación contiene más de un archivo ejecutable, marque el archivo ejecutable principal de esta implementación como la aplicación de inicio seleccionando **Punto de entrada** en la lista desplegable **Tipo de archivo**.  \(Si sólo contiene un archivo ejecutable, MageUI.exe lo marcará para usted.\)  
  
12. Seleccione la ficha **Permisos necesarios** y seleccione el nivel de confianza que la aplicación necesita afirmar.  El valor predeterminado es **Plena confianza**, que se adecuará a la mayoría de las aplicaciones.  
  
13. Seleccione **Archivo**, **Guardar** en el menú, y guarde el manifiesto de aplicación.  Se le solicitará que firme el manifiesto de aplicación al guardarlo.  
  
14. Si tiene un certificado almacenado como un archivo en el sistema de archivos, utilice la opción **Firmar como archivo de certificados** y seleccione el certificado en el sistema de archivos a través del botón de puntos suspensivos \(**...**\).  
  
     O bien  
  
     Si el certificado se guarda en un almacén de certificados al que se puede obtener acceso desde el equipo, seleccione la opción **Firmar con certificado almacenado** y seleccione después el certificado en la lista suministrada.  
  
15. Seleccione **Archivo**, **Nuevo**, **Manifiesto de implementación** en el menú para crear el manifiesto de implementación y, en la pestaña **Nombre**, especifique un nombre y un número de versión \(en este ejemplo, 1.0.0.0\).  
  
16. Cambie a la ficha **Actualizar** y especifique la frecuencia de actualización que desea para esta aplicación.  Si la aplicación utiliza la API de implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para comprobar las actualizaciones, desactive la casilla **Esta aplicación debe buscar actualizaciones**.  
  
17. Vaya a la ficha **Referencia de la aplicación**.  Se pueden rellenar previamente todos los valores de esta ficha haciendo clic en el botón **Seleccionar manifiesto** y seleccionando el manifiesto de aplicación que ha creado en los pasos anteriores.  
  
18. Elija **Guardar** y guarde el manifiesto de implementación en el disco.  Se le solicitará que firme el manifiesto de aplicación al guardarlo.  Haga clic en **Cancelar** para guardar el manifiesto sin firmarlo.  
  
19. Proporcione todos los archivos de la aplicación al cliente.  
  
20. En este punto, el cliente debe firmar el manifiesto de implementación con su propio certificado.  Por ejemplo, si el cliente trabaja para una compañía llamada Adventure Works, puede generar un certificado autofirmado mediante la herramienta MakeCert.exe.  A continuación, utilizará la herramienta Pvk2pfx.exe para combinar los archivos creados por MakeCert.exe en un archivo PFX que se puede pasar a MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Una vez que se ha generado el certificado, el cliente puede firmar el manifiesto de implementación; para ello, debe abrirlo en MageUI.exe y después guardarlo.  Cuando aparezca el cuadro de diálogo de la firma, el cliente debe seleccionar la opción **Firmar como archivo de certificados** y elegir el archivo PFX que guardó en disco.  
  
22. El cliente implementa la aplicación para sus usuarios.  
  
## Pasos siguientes  
  
## Vea también  
 [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)