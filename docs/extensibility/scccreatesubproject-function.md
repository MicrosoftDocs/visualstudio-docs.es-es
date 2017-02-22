---
title: "SccCreateSubProject (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCreateSubProject"
helpviewer_keywords: 
  - "SccCreateSubProject (función)"
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# SccCreateSubProject (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función crea un subproyecto con el nombre especificado en un proyecto principal existente especificado por el `lpParentProjPath` argumento.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 \[entrada, salida\] El nombre de usuario \(hasta SCC\_USER\_SIZE, incluido el terminador NULL\).  
  
 lpParentProjPath  
 \[in\] Cadena que identifica la ruta de acceso del proyecto principal \(hasta SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
 lpSubProjName  
 \[in\] El nombre sugerido subproyecto \(hasta SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
 lpAuxProjPath  
 \[entrada, salida\] Cadena auxiliar que identifica el proyecto \(hasta SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
 lpSubProjPath  
 \[entrada, salida\] Cadena de salida que identifica la ruta de acceso para el subproyecto \(hasta SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Subproyecto se creó correctamente.|  
|SCC\_E\_INITIALIZEFAILED|No se pudo inicializar el proyecto principal.|  
|SCC\_E\_INVALIDUSER|No se pudo iniciar el usuario el sistema de control de código fuente.|  
|SCC\_E\_COULDNOTCREATEPROJECT|No se puede crear el subproyecto.|  
|SCC\_E\_PROJSYNTAXERR|Sintaxis de proyecto no válida.|  
|SCC\_E\_UNKNOWNPROJECT|El proyecto principal es desconocido para el complemento de control de código fuente.|  
|SCC\_E\_INVALIDFILEPATH|Ruta de acceso de archivo no válido o no utilizable.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_CONNECTIONFAILURE|Hubo un problema de conexión de complemento de control de código fuente.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Error no específico.|  
  
## Comentarios  
 Si ya existe un subproyecto con el nombre, la función puede cambiar el nombre predeterminado para crear un único, por ejemplo agregando "\_ \< número \>" a él. El llamador debe estar preparado para aceptar los cambios en `lpUser`, `lpSubProjPath`, y `lpAuxProjPath`. El `lpSubProjPath` y`lpAuxProjPath` a continuación, se usan argumentos en una llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md). No debe modificar el llamador cuando se devuelve. Estas cadenas proporcionan una forma para el complemento de seguimiento de la información que necesita para asociar a un proyecto de control de código fuente. El llamador IDE no mostrará estos dos parámetros al volver, dado que el complemento puede utilizar una cadena con formato que puede no ser adecuada para la visualización. La función devuelve un código de éxito o error y, si es correcto, rellena la variable `lpSubProjPath` con la ruta de acceso completa del proyecto en el nuevo proyecto.  
  
 Esta función es similar a la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), excepto que automáticamente crea un proyecto, en lugar de solicitar al usuario seleccionar uno. Cuando el `SccCreateSubProject` se llama una función, `lpParentProjName` y `lpAuxProjPath` no estarán vacíos y corresponderá a un proyecto válido. Estas cadenas se reciben normalmente por el IDE desde una llamada anterior a la `SccGetProjPath` función o [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 El `lpUser` argumento es el nombre de usuario. El IDE se pasará en el mismo nombre de usuario que anteriormente había recibido de `SccGetProjPath`, y el complemento de control de código fuente debe usar el nombre de forma predeterminada. Si el usuario ya tiene una conexión abierta con el complemento, a continuación, el complemento debe intentar eliminar las peticiones para asegurarse de que funciona en modo silencioso. Sin embargo, si se produce un error en el inicio de sesión, el complemento debe solicitar al usuario para un inicio de sesión y, cuando recibe un inicio de sesión válido, pase el nombre nuevo en `lpUser`. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño \(SCC\_USER\_LEN \+ 1 ó SCC\_USER\_SIZE, que incluye el espacio para el terminador nulo\). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido \(al menos tan válido como la cadena anterior\).  
  
## Notas técnicas de SccCreateSubProject y SccGetParentProjectPath  
 Agregar soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que un usuario debe seleccionar las ubicaciones en el sistema de control de código fuente. Estos cambios se activan mediante Visual Studio si un complemento de control de código fuente admite tanto de las nuevas funciones, `SccCreateSubProject` y `SccGetParentProjectPath`. Sin embargo, puede utilizarse la entrada de registro siguiente para deshabilitar estos cambios y revertir al comportamiento anterior de Visual Studio \(origen de Control de complemento de API versión 1.1\):  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl" \= dword: 00000001  
  
 Si esta entrada del registro no existe o está establecida en DWORD: 00000000, Visual Studio intenta usar las nuevas funciones, `SccCreateSubProject` y `SccGetParentProjectPath`.  
  
 Si la entrada del registro se establece en DWORD: 00000001, Visual Studio no intenta utilizar estas funciones nuevas y las operaciones de agregar al control de código fuente funcionan como lo hacían en versiones anteriores de Visual Studio.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)