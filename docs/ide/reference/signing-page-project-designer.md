---
title: "P&#225;gina Firma, Dise&#241;ador de proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.AddNewStrongNameKey"
  - "ResolveKeySource.KeyFileForSignAssemblyNotImported"
  - "vb.ProjectPropertiesSigning.ChangePasswordDialog"
  - "ResolveKeySource.KeyFileForManifestNotImported"
  - "vb.ProjectPropertiesSigning"
  - "vb.ProjectPropertiesSigning.PasswordNeededDialog"
  - "vb.ProjectPropertiesSigning.PfxPasswordDialog"
helpviewer_keywords: 
  - "Diseñador de proyectos, página Firma"
  - "Página Firma del Diseñador de proyectos"
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# P&#225;gina Firma, Dise&#241;ador de proyectos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice la página **Firma** del **Diseñador de proyectos** para firmar los manifiestos de aplicación y de implementación, así como para firmar el ensamblado \(firma con nombres seguros\).  
  
 Observe que la firma de los manifiestos de aplicación y de implementación es un proceso distinto al de la firma de un ensamblado, aunque ambas tareas se realicen en la página **Firma**.  
  
 Además, el almacenamiento de los datos del archivo de clave difiere en el caso de la firma de manifiestos y de la firma de ensamblados.  En la firma de manifiestos, la información clave se almacena en la base de datos de almacenamiento criptográfica del equipo y en el almacén de certificados de Windows del usuario actual.  En la firma de ensamblados, la información clave sólo se almacena en la base de datos de almacenamiento criptográfica del equipo.  
  
 Para tener acceso a la página **Firma**, seleccione un nodo de proyecto en el **Explorador de soluciones** y, a continuación, haga clic en la opción **Propiedades** del menú **Proyecto**.  Cuando aparezca el **Diseñador de proyectos**, haga clic en la ficha **Firma**.  
  
## Firma de manifiestos de aplicación e implementación  
 casilla de**Firmar los manifiestos de ClickOnce**  
 Active esta casilla para firmar los manifiestos de aplicación y de implementación con un par de claves privada y pública.  Para obtener más información sobre cómo hacerlo, vea [Cómo: Firmar aplicaciones y manifiestos de implementación](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 botón de**Seleccionar del almacn**  
 Le permite seleccionar un certificado existente en el almacén de certificados personales del usuario actual.  Puede seleccionar uno de estos certificados para firmar la aplicación y los manifiestos de implementación.  
  
 Haga clic en **Seleccionar del almacn** abre el cuadro de diálogo de **Seleccionar un certificado** , que enumera los certificados en el certificado personal almacenado que están actualmente válidos \(no expirada\) y que tienen claves privadas.  El propósito del certificado seleccionado debe incluir la firma de código.  
  
 Si hace clic **propiedades del certificado de vista**, el cuadro de diálogo **Detalles del certificado** aparece.  Este cuadro de diálogo incluye información detallada sobre el certificado, e incluye opciones adicionales.  Puede hacer clic en **Obtenga más información sobre los certificados** para ver información adicional de Ayuda.  
  
 botón de**Seleccionar del archivo**  
 Le permite seleccionar un certificado en el archivo de clave existente.  
  
 Haga clic en **Seleccionar del archivo** abre el cuadro de diálogo de **Seleccionar archivo** , que permite seleccionar un archivo de clave del certificado \(.pfx\).  El archivo debe ser protegido mediante contraseña y no se puede estar en el almacén de certificados personal.  
  
 En el cuadro de diálogo de **Escribir contraseña para abrir archivoel archivo** , escriba una contraseña para abrir el archivo de clave del certificado \(.pfx\).  La información de contraseña se almacena en la lista personal de contenedores de claves y en su almacén personal de certificados.  
  
 botón de**Crear certificado de prueba**  
 Permite crear un certificado para probar.  el certificado de prueba se utiliza para firmar la aplicación ClickOnce y los manifiestos de implementación.  
  
 Haga clic en **Crear certificado de prueba** abre el cuadro de diálogo de **Crear certificado de prueba** , en el que se puede escribir una contraseña para el archivo de clave de nombre seguro para el certificado de prueba.  El archivo se denomina *nombreDelProyecto*\_TemporaryKey.pfx.  Si hace clic **Aceptar** sin escribir una contraseña, el archivo .pfx no es contraseña cifrada.  
  
 cuadro de**Direccin URL del servidor de marca de tiempo**  
 Especifica la dirección de un servidor que establece la marca de tiempo de la firma.  Cuando proporciona un certificado, este sitio externo comprueba la hora en la que se firmó la aplicación.  
  
## Firma de ensamblados  
 casilla de**Firmar el ensamblado**  
 Active esta casilla para firmar el ensamblado y crear un archivo de clave de nombre seguro.  Para obtener más información acerca de cómo firmar el ensamblado mediante el **Diseñador de proyectos**, consulte [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/es-es/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 Esta opción utiliza la herramienta Al.exe proporcionada por [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] para firmar el ensamblado.  Para obtener más información sobre Al.exe, consulte [Cómo: Firmar un ensamblado con un nombre seguro](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md).  
  
 lista de**Elija un archivo de clave de nombre seguro**  
 Permite especificar un nuevo o la existencia del archivo de clave de nombre seguro que se utiliza para firmar el ensamblado.  Seleccione **\<Examinar...\>** para seleccionar un archivo de clave existente.  
  
 **\<nuevo…\>**  seleccione para crear un nuevo archivo de clave con el que para firmar el ensamblado.  El cuadro de diálogo de **Crear clave de nombre seguro** aparece, que puede utilizar para especificar un nombre de archivo clave y para proteger el archivo de clave con una contraseña.  La contraseña debe ser por lo menos de 6 caracteres.  Si especifica una contraseña, se crea un archivo de Intercambio de datos personales \(.pfx\); en caso de que no desee especificar ninguna contraseña, se crea un archivo de clave de nombre seguro \(.snk\).  
  
 botón de**Cambiar contraseña**  
 Cambia la contraseña para el archivo de clave de intercambio de datos personales \(.pfx\) que se utiliza para firmar el ensamblado.  
  
 Haga clic en **Cambiar contraseña** abre el cuadro de diálogo de **Cambiar contrasea de clave** .  En este cuadro de diálogo, **Contrasea anterior** es la contraseña actual para el archivo de clave.  **Nueva contraseña** debe ser menos de 6 caracteres.  La información de contraseña se almacena en el almacén de certificados de Windows del usuario actual.  
  
 casilla de**Retrasar firma slo**  
 Active esta casilla para habilitar la firma retardada.  
  
 Tenga en cuenta que un proyecto firmado retardado no se ejecutará y no se podrá depurar.  Sin embargo, puede utilizar la [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) con la opción `-Vr` para omitir la comprobación durante el desarrollo.  
  
> [!NOTE]
>  Al firmar un ensamblado, no siempre puede tener acceso a una clave privada.  Por ejemplo, una organización puede tener un par de claves muy bien guardado que los programadores no tengan acceso todos los días.  La clave pública puede estar disponible, pero la clave privada se limita a algunas personas.  En ese caso, puede utilizar la *firma retardada* o la *firma parcial* para proporcionar la clave pública, difiriendo la suma de la clave privada hasta que se entregue el ensamblado.  
  
## Vea también  
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Administrar la firma de ensamblados y manifiestos](../../ide/managing-assembly-and-manifest-signing.md)   
 [Strong\-Name Signing for Managed Applications](http://msdn.microsoft.com/es-es/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Cómo: Firmar aplicaciones y manifiestos de implementación](../../ide/how-to-sign-application-and-deployment-manifests.md)   
 [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/es-es/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Cómo: Firmar un ensamblado con un nombre seguro](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Ensamblados con nombre seguro](../Topic/Strong-Named%20Assemblies.md)