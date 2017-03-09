---
title: "Administrar la firma de ensamblados y manifiestos | Microsoft Docs"
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
  - "manifiestos [Visual Studio]"
  - "firmar manifiestos [Visual Studio]"
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Administrar la firma de ensamblados y manifiestos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La firma de nombre seguro ofrece una identidad única del componente de software a globalmente.  Los nombres seguros se utilizan para garantizar que el ensamblado no puede ser suplantada por otro usuario, y para garantizar que las dependencias y asignarse componentes de instrucciones de configuración el componente y versión de componente correctos.  
  
 Un nombre seguro está formado por la identidad del ensamblado \(nombre de texto sencillo, número de versión e información de referencia cultural\), además de un token de clave pública y una firma digital.  
  
 Para obtener información sobre cómo firmar ensamblados en proyectos de Visual Basic y C\#, vea [Crear y utilizar ensamblados con nombre seguro](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md).  
  
 Para obtener más información sobre cómo firmar ensamblados en proyectos de Visual C\+\+, consulte [Ensamblados de nombre seguro \(Firma de ensamblados\)](/visual-cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).  
  
## Tipos y firma de activos  
 Puede firmar los ensamblados y los manifiestos de aplicación .NET.  Se incluyen las siguientes:  
  
-   ejecutables \(.exe\)  
  
-   manifiestos de aplicación \(.exe.manifest\)  
  
-   manifiestos de implementación \(.application\)  
  
-   ensamblados de componente compartido \(.dll\)  
  
 Debería firmar los siguientes tipos de activo:  
  
1.  ensamblados, si desea implementarlos en caché global de ensamblados \(GAC\).  
  
2.  Manifiestos de aplicación e implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Permisos de Visual Studio de firma de forma predeterminada para estas aplicaciones.  
  
3.  Ensamblados de interoperabilidad primarios, que se utilizan para la interoperabilidad COM.  La utilidad TLBIMP exige la creación de un nombre seguro al crear un ensamblado de interoperabilidad primario a partir de una biblioteca de tipos COM.  
  
 En general no debe firmar ejecutables.  Un componente con nombre seguro no puede hacer referencia a un componente no\-fuerte\- denominado que se implemente con la aplicación.  Visual Studio no firma ejecutables de la aplicación, pero en su lugar firma el manifiesto de aplicación, que apunta a la aplicación ejecutable sin nombre seguro.  Debe evitar normalmente firmar componentes privados de la aplicación, porque la firma puede dificultar la administración de dependencias.  
  
## Cómo firmar un ensamblado en Visual Studio  
 Se firma una aplicación o componente mediante la pestaña **Firma** de la ventana Propiedades del proyecto \(haga clic con el botón secundario en **Explorador de soluciones** y seleccione **Propiedades**, o escriba las propiedades del proyecto en la ventana **Inicio rápido** , o presionar ALT\+ ENTRAR dentro de la ventana **Explorador de soluciones** \).  Seleccione la ficha **Firma** , active la casilla **Firmar el ensamblado**  .  
  
 Especifique un archivo de clave.  Si decide crear un nuevo archivo de clave, observe que los nuevos archivos de clave siempre se crean en el formato .pfx.  Se necesita un nombre y una contraseña para el nuevo archivo.  
  
> [!WARNING]
>  Siempre debe proteger su archivo de clave con una contraseña para evitar que alguien más lo utilice.  También puede proteger sus claves mediante proveedores o almacenes de certificados.  
  
 También puede señalar a una clave que ha creado.  Para obtener más información sobre cómo crear claves, vea [Cómo: Crear un par de claves privada y pública](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md).  
  
 Si tiene acceso a una clave pública, puede utilizar firma retrasada para diferir la asignación de clave.  Para habilitar la firma retardada activando la casilla **Retrasar firma sólo** .  Un proyecto con firma retrasada no se ejecuta, y no puede depurarlo.  Sin embargo, puede omitir la comprobación durante el desarrollo mediante [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) con la opción `-Vr` .  
  
 Para obtener información sobre cómo firmar manifiestos, consulte [Cómo: Firmar aplicaciones y manifiestos de implementación](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## Vea también  
 [Ensamblados con nombre seguro](../Topic/Strong-Named%20Assemblies.md)   
 [Ensamblados de nombre seguro \(Firma de ensamblados\)](/visual-cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)