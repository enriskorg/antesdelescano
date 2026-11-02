# Antes del escaño

Clasificación de los 350 diputados de la XV Legislatura del Congreso de los Diputados según la experiencia previa que declaran en el **apartado I de su declaración de intereses económicos**. Ese apartado recoge las actividades desarrolladas en los cinco años anteriores a la obtención del mandato.

Las declaraciones de intereses existen desde 2020 (Código de Conducta de las Cortes Generales). Antes solo había declaraciones de bienes y rentas. Para los 133 diputados que ya lo eran en la XIV legislatura se ha leído también la declaración que presentaron entonces, que cubre aproximadamente desde 2014. En ellos la ventana observada es de unos nueve años en lugar de cinco.

La aplicación (`index.html`) muestra el reparto general y por grupo parlamentario, y un listado filtrable con la ficha de cada diputado. Cada ficha incluye el texto extraído y el enlace a la declaración original en congreso.es.

## Población

- 137 diputados que siguen en la Diputación Permanente.
- 213 diputados que cesaron con la disolución de las Cámaras (06/10/2026).

No se incluyen las bajas producidas a lo largo de la legislatura.

## Categorías

| Categoría | Criterio |
|---|---|
| **Experiencia profesional** | En la declaración de la XV o en la de la XIV, declara al menos una actividad en el sector privado o un puesto público no político (funcionario, docente, personal sanitario, magistrado, personal laboral). Puede combinarla con cargos políticos. |
| **Solo política o designación** | Todo lo declarado son cargos electos, cargos de gobierno o de libre designación (ministro, consejero, director general, delegado, jefe de gabinete, asesor o personal eventual), o cargos y empleos en partidos, grupos parlamentarios o la FEMP. También quien no detalla sus actividades y remite a otras declaraciones, y quien no declara ninguna actividad: si no consta otra, su única experiencia es la política. |

Dentro de la experiencia profesional se distinguen tres marcas: privada, pública no política, y si además se declaran cargos políticos.

## Datos

`data/clasificacion.csv` (separador `;`, UTF-8) contiene, por diputado:

- la categoría final y la que resultaría solo con la XV, y si cambia por la XIV;

- formación, grupo parlamentario, circunscripción y situación;
- la categoría asignada y un resumen de lo declarado;
- las dudas de clasificación (ver abajo);
- la fecha y el número de versiones de la declaración;
- el enlace al PDF y el texto obtenido por OCR del apartado I.

## Método

1. Se descargó la versión más reciente de cada declaración desde congreso.es.
2. Los PDF son escaneos: el apartado I se extrajo con OCR (Tesseract, modelo en español).
3. Cada declaración se clasificó leyendo ese texto. Las declaraciones vacías o ilegibles se revisaron sobre la imagen.
4. Para los 133 diputados con declaración en la XIV se leyó también su apartado I (todas las versiones publicadas). 17 diputados que en la XV solo declaraban cargos políticos pasan a experiencia profesional por lo que declararon en la XIV.
5. En los 31 diputados con varias versiones se revisaron también las anteriores. En tres casos la última versión es una modificación que no repite el apartado I y se usó la anterior.

## Limitaciones

- **Ventana de cinco años.** El formulario solo pide lo ocurrido en los cinco años previos al mandato (unos nueve años si hay declaración de la XIV), y solo lo que pueda condicionar la actividad política o haya dado ingresos. «Solo política» significa «solo política en esa ventana», no a lo largo de la carrera.
- **Periodos recortados.** Muchos diputados fechan su actividad desde 2018, el inicio de la ventana, aunque la ejercieran desde antes. Por eso no se puede medir la duración de la experiencia profesional: un periodo corto puede ser real o estar recortado por el formulario.
- **Autodeclaración.** Los datos no están verificados por terceros, y el nivel de detalle varía mucho de unos diputados a otros.
- **OCR.** Puede haber errores de lectura, sobre todo en declaraciones manuscritas. Cada ficha enlaza al original para comprobarlo.

## Casos límite

La columna `caso_limite` señala los casos cuya clasificación depende de un criterio:

| Código | Situación | Criterio aplicado |
|---|---|---|
| `PARTIDO` | Empleo o asesoría en un partido o grupo parlamentario | Experiencia política. Las fundaciones y centros de estudios formalmente independientes del partido (FAES desde 2016) cuentan como privados. |
| `DESIG` | Puesto directivo que puede ser de designación o técnico | Las direcciones y gerencias municipales o de empresas públicas sin plaza de funcionario, y el empleo en la FEMP, son política. La carrera diplomática y consular es profesional. |
| `EXC` | Funcionario o empleado en servicios especiales o excedencia | Profesional: tener la plaza cuenta aunque no se ejerciera en la ventana. |
| `JUB` | Jubilado o retirado | Profesional: la jubilación presupone una carrera previa. |
| `FECHA` | Actividad fuera de la ventana | Los suplentes se miden desde su propio mandato; la experiencia declarada anterior a la ventana cuenta. |
| `MENOR` | Actividad no política marginal (proyecto puntual, asociación, docencia sin retribución, actividad agraria sin remuneración) | Política: no es un empleo. |
| `SINDICAL` | Cargo o empleo sindical | Profesional por el empleo de base, por un empleo técnico en el sindicato o por otra actividad no sindical. Un cargo de dirección sindical sin empleo de base declarado es político. |
| `REMITE` | No detalla y remite a otras declaraciones | Política. |
| `VERSION` | Clasificado con una versión anterior de la declaración | Se usa la anterior porque la última no repite el apartado I. |

## Fuente

Congreso de los Diputados, Registro de Intereses, declaraciones de intereses económicos (XIV y XV Legislaturas): <https://www.congreso.es/busqueda-de-diputados>
