var reproductorAudio = {audioId:"", reproductor:$(".player .wrapper"), audio:""};
var provinciasId = { "02":{ "data-provId":"02", "data-ccaaId":"08", "data-nameCCAA":"Castilla-La Mancha", "data-nameProv":"Albacete"}, "03":{ "data-provId":"03", "data-ccaaId":"10", "data-nameCCAA":"Comunitat Valenciana", "data-nameProv":"Alicante/Alacant"}, "04":{ "data-provId":"04", "data-ccaaId":"01", "data-nameCCAA":"Andalucía", "data-nameProv":"Almería"}, "01":{ "data-provId":"01", "data-ccaaId":"16", "data-nameCCAA":"País Vasco", "data-nameProv":"Araba/Álava"}, "33":{"data-provId":"33", "data-ccaaId":"03", "data-nameCCAA":"Asturias, Principado de", "data-nameProv":"Asturias"}, "05":{ "data-provId":"05", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"Ávila"}, "06":{ "data-provId":"06", "data-ccaaId":"11", "data-nameCCAA":"Extremadura", "data-nameProv":"Badajoz"}, "07":{ "data-provId":"07", "data-ccaaId":"04", "data-nameCCAA":"Balears, Illes", "data-nameProv":"Balears, Illes"}, "08":{ "data-provId":"08", "data-ccaaId":"09", "data-nameCCAA":"Cataluña", "data-nameProv":"Barcelona"}, "48":{ "data-provId":"48", "data-ccaaId":"16", "data-nameCCAA":"País Vasco", "data-nameProv":"Bizkaia"}, "09":{ "data-provId":"09", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"Burgos"}, "10":{ "data-provId":"10", "data-ccaaId":"11", "data-nameCCAA":"Extremadura", "data-nameProv":"Cáceres"}, "11":{ "data-provId":"11", "data-ccaaId":"01", "data-nameCCAA":"Andalucía", "data-nameProv":"Cádiz"}, "39":{ "data-provId":"39", "data-ccaaId":"06", "data-nameCCAA":"Cantabria", "data-nameProv":"Cantabria"}, "12":{ "data-provId":"12", "data-ccaaId":"10", "data-nameCCAA":"Comunitat Valenciana", "data-nameProv":"Castellón/Castelló"}, "51":{ "data-provId":"51", "data-ccaaId":"18", "data-nameCCAA":"Ceuta", "data-nameProv":"Ceuta"}, "13":{ "data-provId":"13", "data-ccaaId":"08", "data-nameCCAA":"Castilla-La Mancha", "data-nameProv":"Ciudad Real"}, "14":{ "data-provId":"14", "data-ccaaId":"01", "data-nameCCAA":"Andalucía", "data-nameProv":"Córdoba"}, "15":{ "data-provId":"15", "data-ccaaId":"12", "data-nameCCAA":"Galicia", "data-nameProv":"Coruña, A"}, "16":{ "data-provId":"16", "data-ccaaId":"08", "data-nameCCAA":"Castilla-La Mancha", "data-nameProv":"Cuenca"}, "20":{ "data-provId":"20", "data-ccaaId":"16", "data-nameCCAA":"País Vasco", "data-nameProv":"Gipuzkoa"}, "17":{ "data-provId":"17", "data-ccaaId":"09", "data-nameCCAA":"Cataluña", "data-nameProv":"Girona"}, "18":{ "data-provId":"18", "data-ccaaId":"01", "data-nameCCAA":"Andalucía", "data-nameProv":"Granada"}, "19":{ "data-provId":"19", "data-ccaaId":"08", "data-nameCCAA":"Castilla-La Mancha", "data-nameProv":"Guadalajara"}, "21":{ "data-provId":"21", "data-ccaaId":"01", "data-nameCCAA":"Andalucía", "data-nameProv":"Huelva"}, "22":{ "data-provId":"22", "data-ccaaId":"02", "data-nameCCAA":"Aragón", "data-nameProv":"Huesca"}, "23":{ "data-provId":"23", "data-ccaaId":"01", "data-nameCCAA":"Andalucía", "data-nameProv":"Jaén"}, "24":{ "data-provId":"24", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"León"}, "25":{ "data-provId":"25", "data-ccaaId":"09", "data-nameCCAA":"Cataluña", "data-nameProv":"Lleida"}, "27":{ "data-provId":"27", "data-ccaaId":"12", "data-nameCCAA":"Galicia", "data-nameProv":"Lugo"}, "28":{ "data-provId":"28", "data-ccaaId":"13", "data-nameCCAA":"Madrid, Comunidad de", "data-nameProv":"Madrid"}, "29":{ "data-provId":"29", "data-ccaaId":"01", "data-nameCCAA":"Andalucía", "data-nameProv":"Málaga"}, "52":{ "data-provId":"52", "data-ccaaId":"19", "data-nameCCAA":"Melilla", "data-nameProv":"Melilla"}, "30":{ "data-provId":"30", "data-ccaaId":"14", "data-nameCCAA":"Murcia, Región de", "data-nameProv":"Murcia"}, "31":{ "data-provId":"31", "data-ccaaId":"15", "data-nameCCAA":"Navarra, Comunidad Foral de", "data-nameProv":"Navarra"}, "32":{ "data-provId":"32", "data-ccaaId":"12", "data-nameCCAA":"Galicia", "data-nameProv":"Ourense"}, "34":{ "data-provId":"34", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"Palencia"}, "35":{ "data-provId":"35", "data-ccaaId":"05", "data-nameCCAA":"Canarias", "data-nameProv":"Palmas, Las"}, "36":{ "data-provId":"36", "data-ccaaId":"12", "data-nameCCAA":"Galicia", "data-nameProv":"Pontevedra"}, "26":{ "data-provId":"26", "data-ccaaId":"17", "data-nameCCAA":"Rioja, La", "data-nameProv":"Rioja, La"}, "37":{ "data-provId":"37", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"Salamanca"}, "38":{ "data-provId":"38", "data-ccaaId":"05", "data-nameCCAA":"Canarias", "data-nameProv":"Santa Cruz de Tenerife"}, "40":{ "data-provId":"40", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"Segovia"}, "41":{ "data-provId":"41", "data-ccaaId":"01", "data-nameCCAA":"Andalucía", "data-nameProv":"Sevilla"}, "42":{ "data-provId":"42", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"Soria"}, "43":{ "data-provId":"43", "data-ccaaId":"09", "data-nameCCAA":"Cataluña", "data-nameProv":"Tarragona"}, "44":{ "data-provId":"44", "data-ccaaId":"02", "data-nameCCAA":"Aragón", "data-nameProv":"Teruel"}, "45":{ "data-provId":"45", "data-ccaaId":"08", "data-nameCCAA":"Castilla-La Mancha", "data-nameProv":"Toledo"}, "46":{ "data-provId":"46", "data-ccaaId":"10", "data-nameCCAA":"Comunitat Valenciana", "data-nameProv":"Valencia/València"}, "47":{ "data-provId":"47", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"Valladolid"}, "49":{ "data-provId":"49", "data-ccaaId":"07", "data-nameCCAA":"Castilla y León", "data-nameProv":"Zamora"}, "50":{ "data-provId":"50", "data-ccaaId":"02", "data-nameCCAA":"Aragón", "data-nameProv":"Zaragoza"} };
var interval;
var cadenaFechas = "";
var arrayFechas = [];
var intervalListenerMap;
var numIntentosCargaMapa = 0;
var numIntentosErroresCargaMapa = 20;
var numElemPorPagDGTCifras = 10;
var contadorNodo,fechaClickNodo;
var camaras,camarasOrderByHighway;
var elemNP = $("#navigationContainer,.btn.btn-warning.fixed-links.icon-people,.tipo-webGenerica,.col-12.ulHtml,footer,.go-top.icon-chevron,.bg-dark,.jumbotron,.alert-info,.carousel-text,[data-type='ModuloDocumentosRelacionados'],.cookiealert,#cconsent-bar");

function mjeInfo(texto){
	if(dataBundle.mjeInfoBool)
		console.log(texto);
}

function mjeDebug(texto){
	if(dataBundle.mjeDebugBool)
		console.log(texto);
}

function replaceAll(texto,remplazarEsto,porEsto){
	return void 0 != texto ? texto.toString().replace(new RegExp(remplazarEsto,"g"),porEsto) : texto;
}

function getAllUrlParams(e){
	/*
	 * ejemplos getAllUrlParams().product; // 'shirt' getAllUrlParams().color; //
	 * 'blue' getAllUrlParams().newuser; // true getAllUrlParams().nonexistent; //
	 * undefined getAllUrlParams('http://test.com/?a=abc').a; // 'abc'
	 */
	var t=e?e.split("?")[1]:window.location.search.slice(1),n={};
	if(t)for(var i=(t=t.split("#")[0]).split("&"),a=0;a<i.length;a++){
		var r=i[a].split("="),o=undefined,s=r[0].replace(/\[\d*\]/,function(e){return o=e.slice(1,-1),""}),c="undefined"==typeof r[1]?"":r[1];s=s.toLowerCase(),c=c.toLowerCase(),n[s]?("string"==typeof n[s]&&(n[s]=[n[s]]),void 0===o?n[s].push(c):n[s][o]=c):n[s]=c
		};
	return n;
}

function getCanonical(){
	var url = window.document.location.href;
	var canonical = $('link[rel=canonical]').attr('href') || $("meta[property='og:url']").attr("content") || '';
	if (canonical.length > 0) {
		if (canonical.indexOf('http') < 0) {
			if (canonical.indexOf('//') !== 0) {
				canonical = window.document.location.protocol + '//' + window.document.location.host + canonical;
		    } else {
			    	canonical = window.document.location.protocol + canonical;
			    }
		}
		url = canonical;
	}
	return url;
}

function getViewport() {
	const width = Math.max(
		document.documentElement.clientWidth,
		window.innerWidth || 0
	)
	if (width <= 576) return 'xs'
	if (width <= 768) return 'sm'
	if (width <= 992) return 'md'
	if (width <= 1200) return 'lg'
	return 'xl'
}

function getBase64ByImage(elem) {
	var img = elem[0];
	var canvas = document.createElement("canvas");
	canvas.width = img.width;
	canvas.height = img.height;
	var ctx = canvas.getContext("2d");
	ctx.drawImage(img, 0, 0);
	var dataURL = canvas.toDataURL("image/png");
	return dataURL;
	// return dataURL.replace(/^data:image\/(png|jpg);base64,/, "");
}

function getBase64ByFileRead(element) {
	var img = element.files[0];
	var reader = new FileReader();
	reader.onloadend = function() {
		$("#convertImg").attr("href",reader.result);
        $("#convertImg").text(reader.result);
        $("#displayImg").attr("src", reader.result);
	}
	reader.readAsDataURL(img);
}

function getFilteredByKey(array, key, value) {
	return array.filter(function(e) {
		return e[key] == value;
	});
}

function getFilteredByWordDGTCifras(array, palabra){
	return array.filter(function(e) {
//		let palabra = getAllUrlParams().q;
		let respuesta = false;
		let valor;
//		Object.keys(array).forEach(function(key) {	
			
			Object.keys(e).forEach(function(key) {
				dataBundle.mjeDebugBool = false;
				valor = false;
				if(typeof e[key] === 'object'){
					Object.keys(e[key]).forEach(function(key2) {
						if(typeof e[key][key2] === 'object'){
							Object.keys(e[key][key2]).forEach(function(key3) {
								valor = containsPAlabraDGTCifras(e[key][key2][key3], palabra);
							});
						} else {
							mjeDebug('-KeyKey2 : ' + key + "->" + key2 + ', -Value: ' + e[key][key2] + " -Palabra:" + palabra);
							valor = containsPAlabraDGTCifras(e[key][key2], palabra);
						}
						if(valor == true){
							respuesta =  true;
						}
					});
				} else{ 
					if(key == 'id' || key == 'url' || key == 'visor' || key == 'url' || key == 'idioma'){
						mjeDebug('Key : ' + key + ', Value:' + e[key] + " ----> No buscamos en este elemento")
					} else {
						mjeDebug('-Key : ' + key + ', -Value : ' + e[key] + ',typeof e[key] === object --> ' + (typeof e[key] === 'object'));
//						let valor = parseToTextSimple(e[key]).includes(parseToTextSimple(palabra));
						valor = containsPAlabraDGTCifras(e[key], palabra);
						if(valor == true){
							respuesta =  true;
						}
					}
				}
				//dataBundle.mjeDebugBool = false;
//				
			});
//		});
		return respuesta;
	});
}

function containsPAlabraDGTCifras(texto, palabra){
	let valor = parseToTextSimple(texto).includes(parseToTextSimple(palabra));
//	mjeDebug("**********************************************************  tiene la palabra = " + parseToTextSimple(palabra) + "--> " + valor)
	return valor;
}

function getFilteredByTagsKeyDGTCifras(array, key, value, separador) {
	return array.filter(function(e) {
		var arrayValores = value.split(separador);
		let respuesta = false;
		if(key == 'fecha'){
			var inicio = parseInt(arrayValores[0]);
			var fin = parseInt(arrayValores[1]); 
			var fecha = parseInt(e.tags[key],); 
			respuesta = (fecha >= inicio && fecha <= fin);
			
		} else {
			respuesta = containsDGTCifras(parseToId(e.tags[key]),arrayValores);
		}
		return respuesta;
	});
}

function containsDGTCifras(texto, arrayValores){
    var value = 0;
    arrayValores.forEach(function(word){
      value = value + texto.includes(word);
    });
    return value >0;
}


function parseToId(nombre){
	nombre = nombre.toLowerCase();
	nombre = replaceAll(nombre," ","-");
	return parseToTextSimple(nombre);
}

function parseToTextSimple(nombre){
	nombre = nombre.toLowerCase();
	nombre = replaceAll(nombre,"á","a");
	nombre = replaceAll(nombre,"é","e");
	nombre = replaceAll(nombre,"í","i");
	nombre = replaceAll(nombre,"ó","o");
	nombre = replaceAll(nombre,"ú","u");
	nombre = replaceAll(nombre,"ñ","n");
	nombre = replaceAll(nombre,"ç","c");
	return nombre;
}


function copyLinkToClipboard(elem){
	var aux = $("#genericModal #textToCopy")[0];
	aux.select();	  // Selecciona el contenido del campo
	var mjeCopy = 'Tu navegador no soporta la función de copiar';
	try {
		document.execCommand("copy");	  // Copia el texto seleccionado
		mjeCopy = 'URL copiada';
	}catch (e) {
		mjeDebug("Error al copiar link al portapapeles");
	}
	var aviso = document.createElement('div');
	aviso.setAttribute('id', 'copyURL');
	aviso.innerHTML = mjeCopy;
	document.body.appendChild(aviso);
	document.load = setTimeout('document.body.removeChild(copyURL)', 2000);
// document.body.removeChild(aux);
}

function copyLinkToClipboardGeneric(id_elemento) {
	var aux = document.createElement("input");
	aux.setAttribute("value", document.getElementById(id_elemento).innerHTML);
	document.body.appendChild(aux);
	aux.select();
	var mjeCopy = 'Tu navegador no soporta la función de copiar';
	try {
		document.execCommand("copy");	  // Copia el texto seleccionado
		mjeCopy = 'Texto Copiado';
	}catch (e) {
		mjeDebug("Error al copiar texto al portapapeles");
	}
	var aviso = document.createElement('div');
	aviso.setAttribute('id', 'copyURL');
	aviso.innerHTML = mjeCopy;
	document.body.appendChild(aviso);
	document.load = setTimeout('document.body.removeChild(copyURL)', 2000);
	document.body.removeChild(aux);
}

function tamVentana() {
	var tam = [0, 0];
	if (typeof window.innerWidth != 'undefined')
	{
		tam = [window.innerWidth,window.innerHeight];
	}
	else if (typeof document.documentElement != 'undefined' && typeof document.documentElement.clientWidth != 'undefined' && document.documentElement.clientWidth != 0)
	{
	    tam = [
	        document.documentElement.clientWidth,
	        document.documentElement.clientHeight
	    ];
	}
	else   {
	    tam = [
	        document.getElementsByTagName('body')[0].clientWidth,
	        document.getElementsByTagName('body')[0].clientHeight
	    ];
	}
	return tam;
}

function isValidCif(cif) {
	if (!cif || cif.length !== 9) {
		return false;
	}

	var letters = ['J', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I'];
	var digits = cif.substr(1, cif.length - 2);
	var letter = cif.substr(0, 1);
	var control = cif.substr(cif.length - 1);
	var sum = 0;
	var i;
	var digit;

	if (!letter.match(/[A-Z]/)) {
		return false;
	}

	for (i = 0; i < digits.length; ++i) {
		digit = parseInt(digits[i]);

		if (isNaN(digit)) {
			return false;
		}

		if (i % 2 === 0) {
			digit *= 2;
			if (digit > 9) {
				digit = parseInt(digit / 10) + (digit % 10);
			}

			sum += digit;
		} else {
			sum += digit;
		}
	}

	sum %= 10;
	if (sum !== 0) {
		digit = 10 - sum;
	} else {
		digit = sum;
	}

	if (letter.match(/[ABEH]/)) {
		return String(digit) === control;
	}
	if (letter.match(/[NPQRSW]/)) {
		return letters[digit] === control;
	}

	return String(digit) === control || letters[digit] === control;
}

function validateDNI(dni) {
    var numero, let, letra;
    var expresion_regular_dni = /^[XYZ]?\d{5,8}[A-Z]$/;

    dni = dni.toUpperCase();

    if(expresion_regular_dni.test(dni) === true){
        numero = dni.substr(0,dni.length-1);
        numero = numero.replace('X', 0);
        numero = numero.replace('Y', 1);
        numero = numero.replace('Z', 2);
        let = dni.substr(dni.length-1, 1);
        numero = numero % 23;
        letra = 'TRWAGMYFPDXBNJZSQVHLCKET';
        letra = letra.substring(numero, numero+1);
        if (letra != let) {
            //alert('Dni erroneo, la letra del NIF no se corresponde');
            return false;
        }else{
            //alert('Dni correcto');
            return true;
        }
    }else{
        //alert('Dni erroneo, formato no válido');
        return false;
    }
}

function listados(){
	if($(".tipo-listado").length){
		actualizaFiltros();
		if($(".tipo-listado .schedule-schedule").length){
			if(getViewport() == 'sm' || getViewport() == 'xs'){ /* Forzamos en la carga de la página que si el dispositivo es pequeño no se vea el modo calendario*/
				$(".schedule-mosaic").show();
				$(".schedule-schedule").hide();
				$.cookie('list-mode-event','schedule-mosaic-bt',{path:'/'});
			}
		};
		
		$(".list-mode a").on("click",function(e){
			e.preventDefault();
			$(".list-mode a").removeClass("active");
			if($(this).parent().hasClass("event-list")){
				$.cookie('list-mode-event',$(this).attr("data-list-type"),{path:'/'});
			} else{
				$.cookie('list-mode',$(this).attr("data-list-type"),{path:'/'});
			}
			$(this).addClass("active");
	// var clase = "col-12 col-sm-6 col-md-12";
	// var dynElem = $(".row.listado > div .dynamic");
			var dynElem = $(".row.listado .dynamic")
			if($(this).hasClass("schedule")){
				$(".schedule-mosaic").hide();
				$(".schedule-schedule").show();
				
			} else if($(this).hasClass("schedule-mosaic-bt")){
				$(".schedule-mosaic").show();
				$(".schedule-schedule").hide();
			} else if($(this).hasClass("mosaic-list")){
				/*
				 * clase = "col-sm-6 col-md-4 col-lg-3"; $(".row.listado > div
				 * .row.no-gutters").addClass("mosaic");
				 * 
				 */
				dynElem.removeClass(dynElem.attr("data-list")).addClass(dynElem.attr("data-mosaic"));
				$(".elem-list",dynElem).hide();
				$(".elem-mosaic",dynElem).show();
				$(".card.link",dynElem).removeClass("news");
			} else {
				/*
				 * $(".row.listado > div
				 * .row.no-gutters").removeClass("mosaic");
				 * 
				 */
				dynElem.removeClass(dynElem.attr("data-mosaic")).addClass(dynElem.attr("data-list"));
				$(".elem-list",dynElem).show();
				$(".elem-mosaic",dynElem).hide();
				$(".card.link",dynElem).addClass("news");
			}
	// $(".row.listado > div").removeClass().addClass(clase);
		});
		
		if($("[data-related='RecursosProveedores']").length == 0){ /* para listado que no son de tipo RecursosProveedores*/
			$('.filter-group .custom-select').on('change', function (e) {
				generaFiltroListado(e);
			});
		}
		
		$(".tags #tags a.badge-pill").on("click",function(e){
			e.preventDefault();
			if($(this).hasClass("active")){
				$(this).removeClass("active");
			} else {
				$(this).addClass("active");
			}
			generaFiltroListado(e,$(".filter-group [type='search']").val());
		});
		
		$(".filter-group .icon-search").on("click",function(e){
			generaFiltroListado(e,$(".filter-group [type='search']").val());
		});
		
		$(".filter-group input[type='search']").on("keyup",function(e){
			if(e.keyCode == '13'){
				generaFiltroListado(e,$(".filter-group [type='search']").val());
			}
		});
		
		/* selector evento calendario en grid */
		$(".one-calendar").on('pickmeup-change', function (e) {
			var selected=e.detail.formatted_date;
			if(selected[0] != selected[1]){
				console.log(e.detail.formatted_date); // New date according to current format
				console.log(e.detail.date);           // New date as Date object
				var url = "rango=" + escape(String(selected).split(",")[0] + "_" +  String(selected).split(",")[1]); // String(selected); escape(String(selected).split(",")[0] + " TO " + String(selected).split(",")[1])
				console.log(url);
				generaFiltroListado(e,"",url);
			}
		});
		
		/* Actualmente no se usa */
		$("#botonSeleccionaRango").on("click",function(e){
			  var selected = pickmeup('.range').get_date(true);
			  var url = "?rango=" + escape(String(selected))
				console.log(url );
				generaFiltroListado(e,"",url);
		});
		/* fin selector evento calendario en grid */
		if($("[data-ocultaRetardado]").length){
			setTimeout(function(){$("[data-ocultaRetardado]").hide()},200);
		}
	}
	
// $(".list-mode").hasClass("event-list"){
//		
// } else {
//		
// }
	
}
function actualizaFiltros(){
	var filtros = String(getAllUrlParams().category ).split("+and+");
	jQuery.each(filtros, function( i, val ) {
		$(".tags #tags a[data-name='" + val + "']").addClass("active");
		if(i == filtros.length -1){	/* en el ultimo elemento guardamos el caso del pais, si coincide se setea */
			$(".custom-select#select-country [value='" + val + "']").attr("selected", "selected");
		}
	});
	if(getAllUrlParams().formato != undefined)
		$(".custom-select#select-type [value='" + getAllUrlParams().formato + "']").attr("selected", "selected");
	if(getAllUrlParams().fecha != undefined)
		$(".custom-select#select-date [value='" + getAllUrlParams().fecha + "']").attr("selected", "selected");
	if(getAllUrlParams().q != undefined){
		$(".filter-group [type='search']").val(getAllUrlParams().q);
	}
	
// filtros.lastIndexOf("+and+");
	
	if(getAllUrlParams().rango != undefined){
		
	}
}

function generaFiltroListado(e,palabraBusqueda,rango){
	var query ="";
	var filtro = "";
	var formato = "";
	var fecha = "";
	palabraBusqueda = palabraBusqueda == undefined ? "" : palabraBusqueda;
	rango = rango == undefined ? "" : rango;
	
	$(".tags #tags a.active").each(function(){
		filtro = filtro == "" ? $(this).attr("data-name") : filtro + "+AND+" + $(this).attr("data-name");
	});
	
	var elemPais = $(".custom-select#select-country");
	if($(" :selected",elemPais).val() != $(" option:first", elemPais).val()){
		filtro = filtro == "" ? $(" :selected",elemPais).val() : filtro + "+AND+" + $(" :selected",elemPais).val();
	}
	
	var elemformato = $(".custom-select#select-type");
	if($(" :selected",elemformato).val() != $(" option:first", elemformato).val()){
		// formato = formato == "" ? $(" :selected",elemformato).val() : formato
		// + "+AND+" + $(" :selected",elemformato).val();
		formato = $(" :selected",elemformato).val();
	}
	
	var elemFecha = $(".custom-select#select-date");
	if($(" :selected",elemFecha).val() != $(" option:first", elemFecha).val()){
		fecha = $(" :selected",elemFecha).val();
	}
	
	
	
	var elemComboResetFiltros = $(".custom-select#select-categoryReset");
	if($(" :selected",elemComboResetFiltros).val() != $(" option:first", elemComboResetFiltros).val()){
		if($(e.currentTarget).attr("id") == 'select-categoryReset'){
			filtro = $(" :selected",elemComboResetFiltros).val(); // si usamos esta opcion, eliminamos los filtos anteriores
		} else{
			filtro = filtro == "" ? $(" :selected",elemComboResetFiltros).val() : filtro + "+AND+" + $(" :selected",elemComboResetFiltros).val();
		}
	}
		
	
	if(palabraBusqueda != "" ){
		query = "q=" + palabraBusqueda;
	}
	if(filtro != ""){
		filtro = "category=" + filtro
		query = query != "" ? query + "&" + filtro : filtro ;
	}
	if(formato != ""){
		query = query != "" ? query + "&formato=" + formato : "formato=" + formato;
	}
	if(fecha != ""){
		query = query != "" ? query + "&fecha=" + fecha : "fecha=" + fecha;
	}
	if(rango != ""){
		query = query != "" ? query + "&" + rango : rango;
	}
	
	
	var url = location.origin + location.pathname + "?" + query; 
	window.location.assign(url);
}


function linkSociales(){
	$(".toolbar .social a,.toolbar .actions a, #collapseFixedLinks .social a, .map .social a").on("click",function(e){
		e.preventDefault();
		var tipo = $(this).attr("class");
		var padre = $(this).parents(".social");
		var lanzaUrl = false;
		var socialURL, ventana;
		var tipoVentana = "_blank";
		var parametros  = "toolbar=yes,scrollbars=yes,resizable=yes,top=250,left=250,width=400,height=600";
		var html = "<p>Preparando Correo</p>";
		mjeInfo(tipo.split(" ")[0]);
		
		switch(tipo.split(" ")[0]){
			case 'icon-twitter-news':
				lanzaUrl = true;
				if($(this).parents().hasClass("socialSideBar") && !$("body").hasClass("caminoDeSantiago")){ /*caso específico para microsite camino de Santiago, no para las páginas de camino de Santiago*/
					parametros = "";
					socialURL = $(this).attr("href");
				} else {
					socialURL = "https://twitter.com/intent/tweet" +
					"?related=DGT&hashtags=DGT&via=DGT" +
					"&text=" + escape($(".b1 h1").text()) + 
					"&url=" + getCanonical();
				}
			break;
		
		
			case 'icon-twitter':
				lanzaUrl = true;
				if($(this).parents().hasClass("socialSideBar") && !$("body").hasClass("caminoDeSantiago")){ /*caso específico para microsite camino de Santiago, no para las páginas de camino de Santiago*/
					parametros = "";
					socialURL = $(this).attr("href");
				} else {
					socialURL = "https://twitter.com/intent/tweet" +
					"?related=DGT&hashtags=DGT&via=DGT" +
					"&text=" + escape($(".b1 h1").text()) + 
					"&url=" + getCanonical();
				}
				break;
			case 'icon-facebook':
			case 'icon-facebook-alt':
				lanzaUrl = true;
				if($(this).parents().hasClass("socialSideBar") && !$("body").hasClass("caminoDeSantiago")){ /*caso específico para microsite camino de Santiago, no para las páginas de camino de Santiago*/
					parametros = ""; 
					socialURL = $(this).attr("href");
				} else {
					socialURL = "https://www.facebook.com/sharer/sharer.php" +
					"?u=" + getCanonical() + getUTM("facebook");
				}
				break;
			case 'icon-mail':
				lanzaUrl = true;
				socialURL = "mailto:?subject=" + $(this).attr("data-info") + " - " +  $(".b1 h1").text() + "&body=" + $(".b1 h1").text() + " " + $(this).attr("data-mje") + getCanonical() + getUTM("email");
				parametros = "top=250,left=250,width=200,height=100";
				break;
			case 'icon-instagram':
			case 'icon-instagram-alt':
				if($(this).parents().hasClass("socialSideBar")){
					lanzaUrl = true;
					parametros = "";
					socialURL = $(this).attr("href");
				} else {
	// lanzaUrl = true;
	// socialURL = "";
					mjeInfo("Actualmente Instagram no permite compartir.");
				}
				break;
			case 'icon-pinterest':
				lanzaUrl = true;
				socialURL = "https://www.pinterest.es/pin/create/button/" +
						"?url=" + getCanonical() +
						"&media=" + "IMAGEN.jpg" +
						"&description=" + $(".b1 h1").text();
				break;
			case 'icon-linkedin':
			case 'icon-linkedin-alt':
				lanzaUrl = true;
				socialURL = "https://www.linkedin.com/shareArticle" +
						"?mini=true" +
						"&url=" + getCanonical() +
						"&title=titulo" + $(".b1 h1").text();
						"&summary=texto" +
						"&source=DGT";
				break;
			case 'icon-whatsapp':
				lanzaUrl = true;
				// socialURL = "whatsapp://send?phone=&text=" + getCanonical();
				// socialURL = "https://wa.me/?phone=&text=" + getCanonical();
				socialURL = "https://api.whatsapp.com/send?phone=&text=" + getCanonical() + getUTM("whatsapp");
				break;
			case 'icon-copy':
				$("#genericModal .modal-text").show();
				$("#genericModal .modal-dialog").removeClass("qr");
				$("#genericModal #qr").hide();
				$("#genericModal .modal-title").text("Obtener vínculo");
				$("#genericModal .modal-text").addClass("mb-0 text-center").html('Pulse en copiar para guardar la URL en el portapapeles <input type="text" id="textToCopy" class="mb-4 mt-3" name="textToCopy" value="' +  getCanonical() + getUTM("copy") + '" readonly><a href="#" class="btn btn-primary">Copiar</a>'); // readonly
				setTimeout(function(){ 
					$("#genericModal #textToCopy").select();	  // Selecciona el contenido del campo
				}, 500);
// aux.setAttribute("value", getCanonical());
				$("#genericModal .modal-text a").on("click",function(e){
					e.preventDefault();
					copyLinkToClipboard("#genericModal #textToCopy");
					$("#genericModal").modal('hide'); 
				});
				
// copyLinkToClipboard();
				break;
			case 'icon-dgt-qr_1':
			case 'icon-dgt-qr_4':
				$("#genericModal .modal-title").text("Obtener vínculo");
				$("#genericModal .modal-text").hide();
				$("#genericModal .modal-dialog").addClass("qr");
				$("#genericModal #qr").show();
				qr();
				break;
			case 'icon-zoom':
			case 'icon-zoom-out':
				/* funcionalidad de ampliar creada en maqueta */
				
				if($(this).hasClass("increase")){
					$(this).removeClass();
					$(this).addClass("icon-zoom-out decrease");
				} else {
					$(this).removeClass();
					$(this).addClass("icon-zoom increase");
				}
				break
			case 'icon-phone':
				tipoVentana = "_self";
				parametros = "";
				lanzaUrl = true;
				socialURL = $(this).attr("href");	
				/* location.origin + "/conoce-la-dgt/donde-estamos/"; */
				break;
			case 'icon-youtube':
				lanzaUrl = true;
				parametros = "";
				socialURL = $(this).attr("href");;
				break;
			case 'icon-alert':
				// este caso se controla en la zona de audio.
				break;
			default:
				mjeDebug("elemento no detectado");
		}
		if(lanzaUrl){
			windowopen(socialURL, tipoVentana, parametros, tipo, html);
		}
		/*
		 * TODO: eliminar esto, se añadio para una presentacion pero hay que
		 * hacerlo bien
		 * ***********************************************************************************************************************************************
		 */
// if($(this).parents().hasClass("socialSideBar")){
// if(document.documentElement.clientWidth >= 992){
// $(".modal-backdrop").click();
// mjeDebug("width = " + document.documentElement.clientWidth);
// mjeDebug("lanzado click modal");
// }
//				
// }
	});
}

function buscar(palabra){
	var urlBuscar = "/buscar.html?q=" + palabra;
	window.open(urlBuscar ,"_self");
}
function buscarDGTCifras(query){
	if(query.charAt(0) != '?')
		query = query.replace('&','?');	// remplaza solo el primer caracter
	var urlBuscar = dataBundle.rutaResultadoCifras + query;
	window.open(urlBuscar ,"_self");
}

function buscador(){
	
	$(".input-group.search .dgt-cifras .btn-primary").on("click",function(e){
		dgtCifrasQuery();
//		buscarDGTCifras("?q=" + $("[type='search']",$(this).parents(".search")).val());
	});
	
	$(".input-group.search :not(.dgt-cifras) .btn-primary").on("click",function(e){
		buscar($("[type='search']",$(this).parents(".search")).val());
	});
	
	$(".input-group.search input[type='search']").on("keyup",function(e){
		if(e.keyCode == '13'){
			if($(this).hasClass("dgtCifras-searcher"))
				dgtCifrasQuery();
			else
				buscar($("[type='search']",$(this).parents(".search")).val());
		}
	});
	
	if($(".tipo-buscador").length){
		// Recuperamos estado despues de la recarga
		if(getAllUrlParams().order != undefined)
			$(".searchSelect [value='" + getAllUrlParams().order + "']").attr("selected", "selected");
		if(getAllUrlParams().filtro != undefined)
			$(".searchSelectFilter [value='" + getAllUrlParams().filtro + "']").attr("selected", "selected");
		
		// Controlamos nuevos click para filtar
		$('.searchSelect').on('change', function () {
			var query = "";
			if(getAllUrlParams().q != undefined){
				query = "q=" + getAllUrlParams().q;
			}
			
			if(getAllUrlParams().category != undefined){
				query = "category=" + getAllUrlParams().category;
			}
			
			var order = "order=" + $(" :selected",".searchSelect").val();
			query += query == "" ? order : "&" + order;
			
			if(getAllUrlParams().filtro != undefined){
				query += (query == "" ? "" : "&" ) + "filtro=" + getAllUrlParams().filtro;
			}
			
			var url = location.origin + location.pathname + "?" + query; 
			window.location.assign(url);
		});
		
		$('.searchSelectFilter').on('change', function () {
			var query = "";
			if(getAllUrlParams().q != undefined){
				query = "q=" + getAllUrlParams().q;
			}
			if(getAllUrlParams().category != undefined){
				query = "category=" + getAllUrlParams().category;
			}
			if(getAllUrlParams().order != undefined){
				query += (query == "" ? "" : "&" ) + "order=" + getAllUrlParams().order;
			}
			
			query += (query == "" ? "" : "&" ) + "filtro=" +  $(" :selected",".searchSelectFilter").val();
			
			var url = location.origin + location.pathname + "?" + query; 
			window.location.assign(url);
		});
		
		
		$(".tab-content").on("click" , ".pagination .page-link",function(e){
			e.preventDefault();
			$(".tabs .tab-content .active .result-list").html('<div class="result-list-body"><div class="loading"><p>Actualizando resultados</p></div></div>');
			
			var url = $(this).attr("href") + "&type=" + $(this).attr("data-type") + "&q=" + $(this).attr("data-q") + "&category=" + $(this).attr("data-category") + "&filter=" + $(this).attr("data-filter") + "&order=" + $(this).attr("data-order") + "&resultadosPorPagina=" + $(this).attr("data-resultadosPorPagina");
			console.log("URL PAG:" + url);
			$.ajax({
				url: url,
				data: "datos=true",
				dataType : 'html',
				success: function(data){
					$(".tabs .tab-content .active .result-list").html($(data).html());
				}
			});
		});
	}
	
	if($(".tipo-listado").length && $("[data-related='RecursosProveedores']").length){	
		$('.tipo-listado').on('change', ".custom-select.select-date", function (e) {
			e.preventDefault();
			let elementoAActualizar = $(this).parents("div.active").attr("data-tipo");
			let fecha = "";
			if(!isNaN($(" :selected",".active .custom-select").val())){
				fecha = "&fecha=" + $(" :selected",".active .custom-select").val();
			}
			var url = location.origin + location.pathname + "?datatipo=" + elementoAActualizar + fecha ; 
			queryRecursosParaProveedores(url);
		});
		
		$("[data-type='Listados'] #nav-tabContent-listadoRecursosProveedores").on("click" , ".pagination .page-link",function(e){
			e.preventDefault();
			let elementoAActualizar = $(this).parents("div.active").attr("data-tipo");
			
			let fecha = "";
			if(!isNaN($(" :selected",".active .custom-select").val())){
				fecha = "&fecha=" + $(" :selected",".active .custom-select").val();
			}
			var url = $(this).attr("href") + "&datatipo=" + elementoAActualizar + fecha;
			queryRecursosParaProveedores(url);
		});
	}
}

function queryRecursosParaProveedores(url){
	mjeDebug(url)
	$(".tabs .tab-content .active").html('<div class="result-list"><div class="loading"><p>Actualizando resultados</p></div></div>');
	$.ajax({
		url: url,
		data: "datos=true",
		dataType : 'html',
		success: function(data){
			let resultado = $("[data-actualizar='true']",$(data)).html()
			$(".tabs .tab-content .active").html(resultado);
		}
	});
}

function windowopen(URL, tipoVentana, parametros, tipo, html){
	ventana = window.open(URL, tipoVentana, parametros, false);
	if(tipo == "icon-mail" || tipo == "abrir-ventana"){
		setTimeout(function(){ventana.document.write(html);mjeDebug("Escribimos ventana de mail")},500);
		setTimeout(function(){ventana.close();mjeDebug("Cerramos ventana de mail")},1500);
	}
}

function googleTranslateElementInit() {
	new google.translate.TranslateElement({pageLanguage: 'es', includedLanguages: 'es,ca,eu,gl,en,fr,de', layout: google.translate.TranslateElement.InlineLayout.SIMPLE}, 'google_translate_element');
}

function translate(){
	let idiomaCookie = $.cookie().googtrans != undefined ? $.cookie().googtrans : "/es/es"
	let elemSelected = $(".contenedorIdiomas [data-comparativa='" + idiomaCookie + "'], .contenedorIdiomasResponsive [data-comparativa='" + idiomaCookie + "']"); 
	elemSelected.addClass("active").attr("aria-selected","true");
	$(".contenedorIdiomas .select>a .code").text(elemSelected.attr("data-code"));
	$(".contenedorIdiomas .select>a .name").text(elemSelected.attr("data-name"));
	$(".contenedorIdiomasResponsive .name").text(elemSelected.attr("data-name"));
	$(".contenedorIdiomasResponsive .nav-title .name").text(elemSelected.attr("data-name"));
	
	$.getScript( '//translate.google.com/translate_a/element.js?cb=googleTranslateElementInit' );
	$('.dropdown.select .dropdown-menu a, .contenedorIdiomasResponsive .dropdown-menu a:not(".back")').click(function(e){
		
		let dominio = location.host.substring(location.host.indexOf("."));
		let idioma = '/es/' + $(this).attr("data-code").toLowerCase();
		$.removeCookie('googtrans', { path: '/' });	//específico para borrar cookie de dominio que añade google
		$.removeCookie('googtrans', { path: '/',domain:'.trafico.es'})
//		$.cookie('googtrans', idioma, { path: '/', domain: location.host });
		$.cookie('googtrans', idioma, { path: '/', domain: dominio });
		location.reload();
	});
}

function calculoTiempoAudio(seconds) {
    sec = Math.floor( seconds );    
    min = Math.floor( sec / 60 );
    min = min >= 10 ? min : '0' + min;    
    sec = Math.floor( sec % 60 );
    sec = sec >= 10 ? sec : '0' + sec;    
    return min + ':' + sec;
}

function getmetadata(elem){
	var audioActual = elem;
	mjeDebug("id = " + audioActual.attr("id") + " --> readyState = " + audioActual[0].readyState);
	var seg = audioActual[0].duration;
	if(!isNaN(seg)){
		var sSeg = calculoTiempoAudio(seg);
		$(".duration",audioActual.parent()).html(sSeg)
		mjeDebug("tiempoAudio = " + seg + " calculado = " + sSeg);
	} else {
		mjeDebug (audioActual.attr("id") + " -->  NaN");
	}
}
function cargaReproductor(id){
	$("body").addClass("media-player");
	reproductorAudio.reproductor.parent().show();
	controlReproductorOld(id);
}

function audio(){
	$("audio").each(function(index, elem) {
		this.addEventListener("loadedmetadata", function(elem){
			getmetadata($(elem.target));	
		});
		/* para firefox */
		if (this.readyState >= 2) {
		      getmetadata($(this));
		}
	});
	
	/* eventos carga audio específico */
	$(".podcast .play a").click(function(e){
		e.preventDefault();
		cargaReproductor($(this).parents(".podcast").attr("id"));
	});
	
	$(".resources .audio button").click(function(e){
		e.preventDefault();
		cargaReproductor($(this).parent().attr("id"));
	});
	
	$(".map, .listadoColaboradores").on("click", ".documento.audio", function(e){
		e.preventDefault();
		cargaReproductor($("audio",$(this)).parent().attr("id"));
	});
	
	$("#collapseFixedLinks .social a.icon-alert").on("click",function(e){
		e.preventDefault();
		if($(".podcast").length){
			$(".podcast .play a").click();
		} else {
			$("body").addClass("media-player");
			reproductorAudio.reproductor.parent().show();
			controlReproductorOld($(this).attr("id"));
		}
	});
	/* Fin eventos carga audio específico */
	
	/* eventos del reproductor */
	$(".play", reproductorAudio.reproductor).click(function(e){
		e.preventDefault();
		playPause();
		controlReproductor();		
	});
	
	$(".backward", reproductorAudio.reproductor).click(function(e){
		e.preventDefault();
		reproductorAudio.audio.currentTime = reproductorAudio.audio.currentTime - 10;
		actualizaBarraProgreso();
	});
	
	$(".forward", reproductorAudio.reproductor).click(function(e){
		e.preventDefault();
		reproductorAudio.audio.currentTime = reproductorAudio.audio.currentTime + 10;
		actualizaBarraProgreso();
	});
	
	$(".close", reproductorAudio.reproductor).click(function(e){
		e.preventDefault();
		reproductorAudio.audio.pause();
		reproductorAudio.reproductor.parent().hide();
		actualizaEstadoReproduccion();
		$("body").removeClass("media-player");
		// TODO: ver si resetear todos los audios al inicio (tiempo 0)
	});
	/* Fin eventos del reproductor */
}

function controlReproductorOld(audioId){
	if(reproductorAudio.audioId != audioId) {
		if(reproductorAudio.audioId != undefined && reproductorAudio.audioId != ""){
			/*
			 * Cambio del audio que se esta reproduciendo
			 */
			// TODO: ver si resetear todos los audios al inicio (tiempo 0)
			reproductorAudio.audio.pause();
			controlReproductor();
			actualizaEstadoReproduccion();
		}
		reproductorAudio.audioId = audioId;
		reproductorAudio.audio = $("audio",$("#" + reproductorAudio.audioId))[0];
		if(!isNaN(reproductorAudio.audio.duration)){
			$(".time span.duration", reproductorAudio.reproductor).html(calculoTiempoAudio(reproductorAudio.audio.duration))
		}
		if($("#" + reproductorAudio.audioId).is('li'))
			$(".title",reproductorAudio.reproductor).text($(".title span","#" + reproductorAudio.audioId).text());
		else if (reproductorAudio.audioId == 'social-icon-alert-boletin')
			$(".title",reproductorAudio.reproductor).text($("#" + reproductorAudio.audioId).attr("data-title"));
		else
			$(".title",reproductorAudio.reproductor).text($(".info h3","#" + reproductorAudio.audioId).text());
	}
	
	playPause();
	controlReproductor();
	actualizaEstadoReproduccion();
}
function playPause(){
	if(reproductorAudio.audio.paused){
		if(reproductorAudio.audio.ended){
			reproductorAudio.audio.currentTime = 0; /*
													 * Para volver a escucharlo
													 * en chrome
													 */
		}
		reproductorAudio.audio.play();
		actualizaEstadoReproduccion();
	} else{
		reproductorAudio.audio.pause();
	}
}

function controlReproductor(){
	if(reproductorAudio.audio.paused){
		$(".play", reproductorAudio.reproductor).addClass("icon-play").removeClass("icon-pause");
		if($("#" + reproductorAudio.audioId).is('li'))
			$("button", "#" + reproductorAudio.audioId).removeClass("icon-pause override");
		else
			$(".play a", "#" + reproductorAudio.audioId).addClass("icon-play").removeClass("icon-pause");
	} else {
		$(".play", reproductorAudio.reproductor).addClass("icon-pause").removeClass("icon-play");
		if($("#" + reproductorAudio.audioId).is('li'))
			$("button", "#" + reproductorAudio.audioId).addClass("icon-pause override");
		else
			$(".play a", "#" + reproductorAudio.audioId).addClass("icon-pause").removeClass("icon-play");
	}
}

function actualizaEstadoReproduccion(){
	actualizaBarraProgreso();
	setTimeout(function(){
		if(reproductorAudio.audio.paused){
			controlReproductor();
		} else {
			actualizaEstadoReproduccion();
		}
	}, 100);
}

function actualizaBarraProgreso(){
	/* tiempo de reproducción actual y progressBar */
	var barraProgreso = (reproductorAudio.audio.currentTime / reproductorAudio.audio.duration).toFixed(3) * 100;
	$(".time span.actual", reproductorAudio.reproductor).html(calculoTiempoAudio(reproductorAudio.audio.currentTime));
	$(".progress .progress-bar", reproductorAudio.reproductor).attr("aria-valuenow", barraProgreso).css("width",barraProgreso+"%");
	/* Fin tiempo de reproducción actual y progressBar */
}

function rrss(){
	if($(".feed-social-network .card-Instagram").length){
		/*$.ajax({
			url: "https://www.instagram.com/DGTES/?__a=1", 
			success: function(result){
				if(result.hasOwnProperty('graphql')){
					mjeInfo("Num Seguidores instagram = " + result.graphql.user.edge_followed_by.count);
					$(".card-Instagram .card-text .text-muted").text(result.graphql.user.edge_followed_by.count);
				}
			}
		});*/
	}
}

/* ir arriba */
function goTop(){ 
	$('.go-top').click(function(e){
		e.preventDefault();
		$('body, html').animate({
			scrollTop: $("body").offset().top
		}, 500);
	});
 
	$(window).scroll(function(){
		if( $(this).scrollTop() > $("main").offset().top ){
			$('.go-top').slideDown(400);
		} else {
			$('.go-top').slideUp(400);
		}
	});
}

function goToAnchor(elem){
	$('body, html').animate({
		scrollTop: elem.offset().top
	}, 500);
	
}
/* fin ir arriba */

function indiceAnclas(){
	$('.indiceAnclas a').click(function(e){
		e.preventDefault();
		goToAnchor($("#" + $(this).attr("href").split("#")[1]));
	});
}

function pagEventosOPunto(){
	if (typeof puntos !== 'undefined'){
		if(puntos.municipio.trim() != "" || puntos.nombre.trim() != "" || puntos.direccion.trim() != "" || puntos.calle.trim() != "" || puntos.numero.trim() != "" || puntos.codigo_postal.trim() != "" || puntos.telefono.trim() != ""){ 
			mostrarInfoMapa();
		}
	}
	
	$("#addToCalendar a").click(function(e){
		if(!$(this).hasClass("icon-ical")){
			e.preventDefault();
		}
		let lanzaUrl = true;
		let tipoVentana = "_blank";
		let parametros = "";
		let html = "";
		var inicio = eventos.horario.inicio.anyo + eventos.horario.inicio.mesNum + eventos.horario.inicio.dia + "T" + eventos.horario.inicio.hora.replace(':', '') + "00";
		var fin = eventos.horario.fin.anyo + eventos.horario.fin.mesNum + eventos.horario.fin.dia + "T" + eventos.horario.fin.hora.replace(':', '') + "00";
		var localizacion = "Online";
		if(eventos.formato != 'Online'){
			if(evento.localizacion != ''){
				localizacion = evento.localizacion; 
			} else if (eventos.mapa.mapCoord.latitud != '') {
				localizacion = eventos.mapa.mapCoord.latitud + "," + eventos.mapa.mapCoord.longitud;
			} else {
				localizacion = "";
			}
		}
		switch($(this).attr("class")){
			case 'icon-outlook':
				URL = "https://outlook.live.com/owa/?path=%2Fcalendar%2Faction%2Fcompose" 
					+ "&rru=addevent"
					+ "&startdt=" + inicio
					+ "&enddt=" + fin
					+ "&subject=" + eventos.titulo
					+ "&body=" + eventos.descripcion
					+ "&location=" + localizacion;
				break;
			case 'icon-google-calendar':
				URL = "https://calendar.google.com/calendar/u/0/r/eventedit?action=TEMPLATE"
						+ "&text=" + eventos.titulo 
						+ "&dates=" + inicio + "/" + fin
						+ "&ctz=Europe/Madrid"
						+ "&details=" + eventos.descripcion
						+ "&location=" + localizacion
						+ "&add=" /* añadir correos */
						+ "&pli=1"
						+ "&sf=true";
				break;
			case 'icon-ical':
				lanzaUrl = false;
				/* funcionalidad en el propio boton */
// URL = "/export/descargas/ics/eventoDGT.ics";
				break;
			case 'icon-yahoo':
				URL="https://calendar.yahoo.com/?v=60" 
					+ "&title=" + eventos.titulo 
					+ "&st=" + inicio
					+ "&et=" + fin
					+ "&desc=" + eventos.descripcion
					+ "&in_loc=" + localizacion;
				break;
			default:
				lanzaUrl = false;
				mjeDebug("Caso no contemplado");
		}
		mjeInfo(URL);
		if(lanzaUrl){
			windowopen(URL, tipoVentana, parametros, "" , "");
		}
	});
}

function BORRAR(){
	
//	$(".dgtCifras-searcher").click(function(e){
//		console.log("prueba")
//	})
	
	
	
	/* pruebas y emulaciones */
	/* caso de ir a página */
	/*
	 * $("[data-type='Listados'] a").click(function(e){ e.preventDefault();
	 * switch($(this).parents(".container").attr("data-related")){ case
	 * 'Noticia': var pagina = $(this).attr("href").substring(0,
	 * $(this).attr("href").length-1); pagina =
	 * pagina.substring(pagina.lastIndexOf("/"), pagina.length); var url =
	 * "/actualidad/noticias" + pagina; window.open(url, "_self", "", false);
	 * break default: } });
	 */
	
//	/* Para xxx en las pruebas buscador */
//	if(getAllUrlParams().tab != undefined){
//		$("#"+getAllUrlParams().tab).click();
//	};
}
function avisoAlertasHome(){
	var avisos = $.cookie("avisoID") != undefined ? $.cookie("avisoID") : '';
	if($("body").hasClass("online")){ /*
										 * solo ocultamos los avisos en modo
										 * online
										 */
		$(".AvisoHome").each(function(){
			if(!avisos.includes($(this).attr("id"))){
				$(this).show();
			}
		});
	}
	$('.AvisoHome .close').click(function(e){
		$.cookie("avisoID", ($.cookie("avisoID") != undefined ? $.cookie("avisoID") : '') + $(this).parents(".AvisoHome").prop("id") + "|"); // cookie de sesión
	});
}
function cookies(){
	if($.cookie("AC")){
		$(".cookies-section").hide();
	}
	$(".cookies-section #cookies-section-accept").click(function(e){
		e.preventDefault();
		var anyo = new Date(new Date().getTime() + 365 * 24 * 3600 * 1000);
		$.cookie("AC","true",{expires: anyo, path:'/'});
		$(".cookies-section").hide();
	});
}

function lanzaPopOver(){
	$('[data-toggle="popover"]').click(
		function(e){
			e.preventDefault()
		}
	);
	$('[data-toggle="popover"]').popover(
	        {'placement':'bottom',
	         'content':function() {
	        	 var elem = $("#"+$(this).attr("data-id")).html();
	        	 mjeInfo(elem);
	             return elem;
	        },
	         'html':true
	        }
	    );
}
function selectCountryStaticHtml(){
	/* script especifico para html statico añadido en canjes */
	 $('.selectCountryStaticHtml').on('change', function () {
         window.location = $(this).val();
     });
	 
	 if ($(".b1 .titleCountry").length) {
		 var texto = decodeURI(getAllUrlParams().pais);
		 if(texto != 'undefined'){
			 $(".b1 .titleCountry").html(texto);
		 }
       }
}

function modalEvent(fecha){
	let eventosDia = calendarEvents.filter(n => n.start == fecha);
	if(eventosDia.length > 0){
		
		var cadenaEventos = "";
		$.each(eventosDia,function(){
// classNames: "border-info"
// end: "2020-07-22"
// start: "2020-07-22"
// title: "Coloquio con Dª Natalia Chueca. Consejera de Servicios Públicos y
// Movilidad del Ayuntamiento de Zaragoza"
// url:
// "Coloquio-con-D-Natalia-Chueca.-Consejera-de-Servicios-Publicos-y-Movilidad-del-Ayuntamiento-de-Zaragoza"
			cadenaEventos +=	'<div class="card link event">'
									+ '<a href="' + this.url + '">'
									+ '<div class="card-body">'
										+ '<p class="card-title">' + this.type + '</p>'
										+ '<p class="card-text">' + this.title +'</p>'
										+ '<p class="card-text text-muted">'
											+ '<small>' + paseDate(this.start) + ', ' + $($(this.time)[2]).text() +'</small>'
											+ '<small>' + this.location + '</small>'
										+ '</p></div></a></div>';
		});
		$("#modalDayDetail #modalDayDetailLabel").html(paseDate(fecha, "titulo") + "<span>" + eventosDia.length + " evento" + (eventosDia.length == 1 ? '' : 's')  + "</span>"); // Lunes 1 Enero 2020 <span>6 eventos</span>
		$(".modal-body").html(cadenaEventos);
		$('#modalDayDetail').modal('show');
	}
}

function paseDate(fecha, tipo ){
	var newDate = "";
	moment.locale("es");
	switch(tipo){
		case 'titulo':
			newDate = moment(fecha).format('dddd DD MMMM YYYY');
			break;
		/*
		 * case 'numerico': newDate = moment(fecha).format('dddd DD MMMM YYYY');
		 * break;
		 */
		default:
			newDate = moment(fecha).format('L');
	}
	return newDate;
}

function qr(){
	$("#dynamic").html($('<img id="imgQR1" src="' + dataBundle.imgQR + '" style="display:none" />')[0]);
	setTimeout(function(){
		$("#genericModal #qr").html("");
		$("#genericModal #qr").qrcode({
		    // render method: 'canvas', 'image' or 'div'
		    render: 'canvas',
	
		    // version range somewhere in 1 .. 40
		    minVersion: 3,
		    maxVersion: 40,
	
		    // error correction level: 'L', 'M', 'Q' or 'H'
		    ecLevel: 'M',
	
		    // offset in pixel if drawn onto existing canvas
		    left: 0,
		    top: 0,
	
		    // size in pixel
		    size: 250,
	
		    // code color or image element
		    fill: '#0057a6',// '#000',
	
		    // background color or image element, null for transparent
			// background
		    background: null,
	
		    // content
		    text: getCanonical() + getUTM("qr"),
	
		    // corner radius relative to module width: 0.0 .. 0.5
		    radius: 0,
	
		    // quiet zone in modules
		    quiet: 0,
	
		    // modes
		    // 0: normal
		    // 1: label strip
		    // 2: label box
		    // 3: image strip
		    // 4: image box
		    mode: 4,
	
		    mSize: 0.14,
		    mPosX: 0.5,
		    mPosY: 0.5,
	
		    label: 'no label',
		    fontname: 'sans',
		    fontcolor: '#000',
	
		    image: $("#dynamic #imgQR1")[0]// imgBase64
		});
	},50)
}

function getUTM(type){
	return (getCanonical().includes("?") ? "&" : "?") + "utm_medium=" + type + "&utm_source=DGT&utm_campaign=web";;
}

function dgtCifrasQuery(selizq = false) {
	//getMultipleSelectionIds();
	let q = $(".dgtCifras-searcher").val() != "" ? "?q=" + $(".dgtCifras-searcher").val() : ""; 
	let tema = "";
	let categoria = "";
	let formato = "";
	let fecha = "";
	let mapa = "";
	let pagina = "&pag=" + (isNaN(Number.parseInt($("#actualPage").text())) || $("#actualPage").text() == '0' ? 1 : Number.parseInt($("#actualPage").text()));
	if($(".tipo-DGTCifras").length){
		$(".cifras-filters input:checked").each(function(){
			tema += tema == "" ? "&tema=" + $(this).attr("value") : "|" + $(this).attr("value");
		});
	}
	console.log("Pulsado en " + $("p",$(this)).text() + " del tag = " +  $("p",$(this)).attr("data-type") + " con id = " +$("p",$(this)).attr("id")) ;
	
	if($(".tipo-DGTCifras-Listado").length){
		$("input:checked").each(function(){
			switch($(this).attr("data-type")){
				case 'cCategoria':
					categoria += categoria == "" ? "&categoria=" + $(this).prop("id") : "|" + $(this).prop("id");
					//console.log("SLL es categoria " + $(this).prop("id"));
					break;
				case 'cTema':
					tema += tema == "" ? "&tema=" + $(this).prop("id") : "|" + $(this).prop("id");
					//console.log("SLL es tema " + $(this).prop("id"));
					break;				
				case 'cFormato':
					formato += formato == "" ? "&formato=" + $(this).prop("id") : "|" + $(this).prop("id");
					break;
				case 'cFecha':
					fecha += fecha == "" ? "&fecha=" + $(this).prop("id") : "|" + $(this).prop("id");
					break;
				default:
					console.log("filtro no detectado");
			}
		});
		var elemFecha = $('#cFecha .scale ins');
		let fechasRango = $(elemFecha[0]).text() + "," + $(elemFecha[1]).text();
		if(fechasRango != $(".range-slider").val())
			fecha += "&fecha=" + $(".range-slider").val();
		/*console.log("Tema = " + tema);
		console.log("categoria = " + categoria);
		console.log("formato = " + formato);
		console.log("fecha = " + fecha);*/
	}
	interval = setInterval(function(){	// esperamos a que el mapa nos devuelva
										// respuesta
		if(codsINE != undefined){ 
			let correcto = false;		
			if(codsINE.length > 0){
				mapa = "&mapa=" + codsINE.toString();
				correcto = true;
			}
//			else if(codsINE.length == 0 && codsINETemp != undefined && codsINETemp.length > 0 ){ /* No dio tiempo a respuesta por parte del mapa, pero tenemos el cambio que se hizo en el filtro de DGT en cifras en codsINETemp*/
//				mapa = "&mapa=" + codsINETemp.toString();
//				correcto = true;
//			}
			else if(codsINE.length == 0 && $(".tagTipoMapa").length > 0) { // este caso es que habria un error porque no dio tiempo al mapa a actualizarse
				mjeDebug("Detectado posible Error: numIntentosCargaMapa = " + numIntentosCargaMapa);
				if(numIntentosCargaMapa >= numIntentosErroresCargaMapa){	// si tras el numero de intentos no se ha cargado el mapa, recargamos la página sin datos del mapa
					correcto = true;
				}
				numIntentosCargaMapa++;
			}
			else{
				correcto = true;
			}
			if(correcto){
				clearInterval(interval);
				let order = "&order=" + ($(".custom-select :selected").val() != undefined ? $(".custom-select :selected").val() : "DESC");
				var query = q + mapa + tema + categoria + formato + fecha + pagina + order;				
				buscarDGTCifras(query);
			}
		} else {	// Fallo porque no carga el mapa
			mjeDebug("Detectado posible Error, no carga mapa: numIntentosCargaMapa = " + numIntentosCargaMapa);
			if(numIntentosCargaMapa >= numIntentosErroresCargaMapa){
				codsINE = [];	// si tras el numero de intentos no se ha cargado el mapa, recargamos la página sin datos del mapa
			}
			numIntentosCargaMapa++;
		}
	}, 300);
}

var contadorDGTCifras;
function DGTCifras(){
	var rutaResultadoCifras = dataBundle.rutaResultadoCifras;	// "/menusecundario/dgt-en-cifras/dgt-en-cifras-resultados/";
	var rutaVisorCifras = dataBundle.rutaVisorCifras;		// "/menusecundario/dgt-en-cifras/dgt-en-cifras-resultados/dgt-en-cifras-detalle/dgt-en-cifras-visor/";
	let URLCifrasJson = dataBundle.URLCifrasJson;			// "/.content/.assets/json/DGT-cifras.json";
	
// $("#selectoresTags").on("click",function(e){
// e.preventDefault();
// });
	$('input.dgtCifras-searcher[type=search]').on('search', function () { /* aspa de borrar en buscador de DGT en cifras */
	    // search logic here
	    // this function will be executed on click of X (clear button)
//		dgtCifrasQuery();
	});
	
	if($(".tipo-DGTCifras").length){
		$(".infoSection .buttonAccederDGTCifras, .multiCollapse .buttonAccederDGTCifras").on("click",function(e){
			e.preventDefault();
			dgtCifrasQuery();
		});
		
		
		
		$.ajax({
			url: URLCifrasJson,
			dataType : 'json',
			success: function(data){
// mjeInfo(data);
				listado = data;	// $.parseJSON(data)
				// var array = [{aaa:"sss",fecha_actualizacion:
				// "25-04-2021",tags:{aaa:"asdf",vvv:"asdf"}},{aaa:"sss",fecha_actualizacion:
				// "29-04-2021",tags:{aaa:"asdf",vvv:"asdf"}},{aaa:"sss",fecha_actualizacion:
				// "13-04-2021",tags:{aaa:"asdf",vvv:"asdf"}}]
				var sortedArray  = listado.sort((a,b) => new moment(a.fecha_actualizacion, 'DD-MM-YYYY') - new moment(b.fecha_actualizacion, 'DD-MM-YYYY'));
				sortedArray.reverse();
				
				$(".ultimosDatosPublicados").html("");
				var temp = $.trim($('#ultimosDatosPlantilla').html());
                $.each(sortedArray, function (index, obj) {
                    var x = temp.replace(/{{templ_url}}/ig, obj.url);
                    x = x.replace(/{{templ_titulo}}/ig, obj.titulo);
                    x = x.replace(/{{templ_extension}}/ig, obj.tags.formato);
                    $('.ultimosDatosPublicados').append(x);
                    
                	return (index + 1 < 3);
                });
// console.log(sortedArray)
			},
			error: function( jqXHR, textStatus, errorThrown ) {
				    mjeDebug( 'Error: ' + textStatus );
			
			}
		});
	}
	if($(".tipo-DGTCifras-Listado").length){
		if(replaceAll(replaceAll($("#contenedorTags").html(),"\t",""),"\n","") == ""){ //si la nube de tags esta vacia ocultamos contenedor
			$(".tags #tags").hide();
		}
		$(".filter-group .borrarFiltros").on("click",function(e){
			buscarDGTCifras("");
		});
		$(".pagination .page-link").on("click",function(e){
			e.preventDefault();
			if(!$(this).parent().hasClass("disabled")){
				let actualPage = Number.parseInt($("#actualPage").text());
				let limitPage = Number.parseInt($("#limitPage").text());
				if($(this).parent().hasClass("pagePrev")){
					if(actualPage - 1 >= 1){
						$("#actualPage").text(--actualPage);
					}
				} else if($(this).parent().hasClass("pageNext")){
					if(actualPage + 1 <= limitPage){
						$("#actualPage").text(++actualPage);
					}
				} else if($(this).parent().hasClass("pageInit")){
					$("#actualPage").text("1");
					
				} else if($(this).parent().hasClass("pageLast")){
					$("#actualPage").text(limitPage);
				}
				estadoPaginadoDGTCifras(actualPage,limitPage);
				dgtCifrasQuery();
			}
		});
		$("#selectoresTags").on("click", ".li-nb div", function(e){
			e.preventDefault();
			$("#actualPage").text(1); //reseteamos paginado.
			console.log("Pulsado en " + $("p",$(this)).text() + " del tag = " +  $("p",$(this)).attr("data-type") + " con id = " +$("p",$(this)).attr("id")) ;
			setTimeout(function(){dgtCifrasQuery(true)},50); 	// Damos tiempo a que se ponga el checked
		});
		$("#tags a").on("click", function(e){
			e.preventDefault();
			if($(this).hasClass("tagTipoFecha")){
// 				let arrayFechas = cadenaFechas.split(",");
				$(".range-slider").val(arrayFechas[0] + "," + arrayFechas[arrayFechas.length-1]);
			} else if($(this).hasClass("tagTipoMapa")){
				if(codsINE == undefined){/* Fallo porque no cargo todavía el mapa, lo sacamos de la URL */
					codsINE = codsINETemp = getAllUrlParams().mapa.split(","); 
				}
				codsINETemp.splice(codsINE.indexOf($(this).attr("data-cod")),1);
//				codsINE.splice(codsINE.indexOf($(this).attr("data-cod")),1); /* not working */
				codsINE = codsINETemp; 
				
				clearInterval(intervalListenerMap);
				clearMultipleSelection();
				setMultipleSelectionActiveItems('Limite_admin_prov', codsINETemp);
				/* Por problemas de respuesta desde mapa forzamos la carga en el caso de eliminar tag de tipo mapa*/
				window.location.href = window.location.href.replace(/(mapa=).*?(&)/,'$1' + codsINETemp.toString() + '$2');
			} else{
				$("#" + $(this).attr("data-cod")).removeAttr('checked');
			}
			dgtCifrasQuery();
		});
		$('.filter-group .custom-select').on('change', function () {
			dgtCifrasQuery();
		});
		
		setTimeout(function(){ /*damos un delay esperando a que el mapa responda y se setee la configuracion para evitar errores */
			intervalListenerMap = setInterval(function(){	// esperamos a que el mapa nos devuelva la respuesta getMultipleSelectionIds(), y se vuelve a preguntar constantemente
				getMultipleSelectionIds();
				if(codsINE != undefined){ 
	//				clearInterval(intervalListenerMap);
					if(codsINETemp != undefined){
						if(codsINETemp.toString() != codsINE.toString()){
							dgtCifrasQuery();
						}
					} else {
						codsINETemp = codsINE;
					}
				}
			}, 1500);
		},4000);
		
		/*var tiposTema = {	
			"cifras-de-siniestralidad":"icon-dgt-cifras-1#Cifras de siniestralidad#cifras-de-siniestralidad",
			"distintivos-ambientales":"icon-dgt-ocbe#Distintivos ambientales#distintivos-ambientales",
			"controles-de-trafico":"icon-dgt-control#Controles de tráfico#controles-de-trafico",
			"incidencias-de-trafico":"icon-dgt-incidentes#Incidencias de tráfico#incidencias-de-trafico",
			"informacion-municipal":"icon-dgt-informes#Información municipal#informacion-municipal",
			"accidentes-de-trafico":"icon-dgt-accidentes-trafico#Accidentes de tráfico#accidentes-de-trafico",
			"conductores":"icon-dgt-conduccion#Conductores#conductores",
			"vehiculos":"icon-car#Vehículos#vehiculos"
		};*/
		var tiposTema = {	
			"Información municipal":"icon-dgt-informes#Información municipal#informacion-municipal",
			"Denuncias e ingresos":"icon-dgt-incidentes#Denuncias e ingresos#denuncias-e-ingresos",
			"Accidentes de tráfico":"icon-dgt-accidentes-trafico#Accidentes de tráfico#accidentes-de-trafico",
			"Conductores":"icon-dgt-conduccion#Conductores#conductores",
			"Vehículos":"icon-car#Vehículos#vehiculos"
		};
		/*
		 "Incidencias de tráfico":"icon-dgt-incidentes#Incidencias de tráfico#incidencias-de-trafico",
		 "Cifras de siniestralidad":"icon-dgt-cifras-1#Cifras de siniestralidad#cifras-de-siniestralidad",
		 "Distintivos ambientales":"icon-dgt-ocbe#Distintivos ambientales#distintivos-ambientales",
		 "Controles de tráfico":"icon-dgt-control#Controles de tráfico#controles-de-trafico",
		*/
		let idsMapa = getAllUrlParams().mapa;
		let provincias = [];
		if(idsMapa != "" && idsMapa != undefined){
			$.each(idsMapa.split(","),function(index,value){
				provincias.push(this);
			});
			setTimeout(function(){
//				setActiveItems('Limite_admin_prov',provincias);
				setMultipleSelectionActiveItems('Limite_admin_prov', provincias)
			},3000);
		}
		$(".tagTipoMapa").each(function(){
			$(this).text(provinciasId[$(this).attr("data-cod")]["data-nameProv"]);
		});
		let cTema = {};
		let cFormato = {};
		let cFecha = {};
		let cFechaRangoMax = {};
		let cCategoria = {};
		$.ajax({
			url: URLCifrasJson,
			dataType : 'json',
			success: function(data){
// 				mjeInfo(data);
				listado = data;	// $.parseJSON(data)
				var sortedArray  = listado.sort((a,b) => new moment(a.fecha_actualizacion, 'DD-MM-YYYY') - new moment(b.fecha_actualizacion, 'DD-MM-YYYY'));
				if(getAllUrlParams().order != 'asc'){
					sortedArray.reverse();
				}
				
				$.each(sortedArray, function (index, obj) {
					$.each(obj.tags.fecha.split(","),function(){
						cFechaRangoMax[this.toUpperCase()] != undefined ? cFechaRangoMax[this.toUpperCase()]++ : cFechaRangoMax[this.toUpperCase()] = 1;
                	});
				});
				
				Object.keys(cFechaRangoMax).forEach(function(key) {
     		    	arrayFechas.push(key)
				});
				
				var sortedAndFiltredArray = sortedArray;
				
				
				if(getAllUrlParams().q != undefined && getAllUrlParams().q != ""){
					sortedAndFiltredArray= getFilteredByWordDGTCifras(sortedAndFiltredArray, decodeURI(getAllUrlParams().q));
				}
				if(getAllUrlParams().tema != undefined && getAllUrlParams().tema != ""){
					sortedAndFiltredArray= getFilteredByTagsKeyDGTCifras(sortedAndFiltredArray, "tema", getAllUrlParams().tema,"|");
				}
				if(getAllUrlParams().categoria != undefined && getAllUrlParams().categoria != ""){
					sortedAndFiltredArray= getFilteredByTagsKeyDGTCifras(sortedAndFiltredArray, "categoria", getAllUrlParams().categoria,"|");
				}
				if(getAllUrlParams().formato != undefined && getAllUrlParams().formato != ""){
					sortedAndFiltredArray= getFilteredByTagsKeyDGTCifras(sortedAndFiltredArray, "formato", getAllUrlParams().formato,"|");
				}
				if(getAllUrlParams().fecha != undefined && getAllUrlParams().fecha != "" && getAllUrlParams().fecha != ","){
					sortedAndFiltredArray = getFilteredByTagsKeyDGTCifras(sortedAndFiltredArray, "fecha", getAllUrlParams().fecha,",");
				}
				if(getAllUrlParams().mapa != undefined && getAllUrlParams().mapa != ""){
					sortedAndFiltredArray = getFilteredByTagsKeyDGTCifras(sortedAndFiltredArray, "mapa", getAllUrlParams().mapa,",");
				}
                
				$("#numResultados").html(sortedAndFiltredArray.length + " Resultado" + (sortedAndFiltredArray.length == 1 ? '' : 's'));
				/* ******************************************************* *
				** Pintamos Filtros laterales (sin aplicar la paginación)  *
				** ******************************************************* */
				dataBundle.mjeDebugBool = true;
				$.each(sortedAndFiltredArray, function (index, obj) {
					$.each(obj.tags.tema.split(","),function(){
    					let temaActual;
    					try {
    						temaActual = tiposTema[this].split("#");
    						cTema[temaActual[2]] != undefined ? cTema[temaActual[2]]++ : cTema[temaActual[2]] = 1;
						} catch(err) {
						  mjeDebug("ERROR: " + err.message);
						  mjeDebug("ERROR: this = " + this);
						}
    				});
                	$.each(obj.tags.formato.split(","),function(){
                		cFormato[this.toUpperCase()] != undefined ? cFormato[this.toUpperCase()]++ : cFormato[this.toUpperCase()] = 1;
                	});
                	$.each(obj.tags.fecha.split(","),function(){
                		cFecha[this.toUpperCase()] != undefined ? cFecha[this.toUpperCase()]++ : cFecha[this.toUpperCase()] = 1;
                	});
                	$.each(obj.tags.categoria.split(","),function(){
                		cCategoria[this] != undefined ? cCategoria[this]++ : cCategoria[this] = 1;
                	});
				});
                contadorDGTCifras = {cTema,cCategoria,cFormato,cFecha};
                var htmlCat, htmlFecha,htmlFormato;
                var temp = $.trim($('#selectoresPlantilla').html());
                var tempResp = $.trim($('#selectoresPlantillaresponsive').html());
				
        		Object.keys(contadorDGTCifras).forEach(function(key) {
        		    Object.keys(contadorDGTCifras[key]).forEach(function(key2) {
        		    	var value = contadorDGTCifras[key][key2];
						var escategoria = false;
						
        		    	switch(key){
        		    		case 'cTema':
        		    			$(".result-search ",$("." + key2).parent()).html(value);
								//console.log("SLL " + key2 + " value:" + value);
        		    			break;
        		    		case 'cCategoria':	
								escategoria = true;
        		    		case 'cFormato':
        		    			let parsedId = parseToId(key2.toLowerCase());
								//console.log("SLL2 " + key2);
        		    			let clase = "";
								/*
        		    			if(JSON.stringify(getAllUrlParams()).includes(parsedId)){
        		    				clase = "active";
        		    			}
								*/
								
								if(escategoria) {
									console.log("categoria:"  + getAllUrlParams().categoria);
									if(getAllUrlParams().categoria == parsedId) {
										clase = "active";
									}
								} else {
									if(getAllUrlParams().formato == parsedId) {
										clase = "active";
									}
								}
								//console.log("SLL2 JSON " + JSON.stringify(getAllUrlParams()));
        		    			var x = temp.replace(/{{templ_id}}/ig, parsedId);
        	                    x = x.replace(/{{templ_title}}/ig, key2);
        	                    x = x.replace(/{{templ_type}}/ig, key);
        	                    x = x.replace(/{{templ_num}}/ig, value);
        	                    x = x.replace(/{{templ_click}}/ig, clase == 'active' ? 'clicked' : '');
        	                    x = x.replace(/{{templ_clase}}/ig, clase);
        	                    $("#" + key + ' ul').append(x);
        	                    
        	                    var y = tempResp.replace(/{{templ_id}}/ig, parsedId);
        	                    y = y.replace(/{{templ_title}}/ig, key2);
        	                    y = y.replace(/{{templ_type}}/ig, key);
        	                    y = y.replace(/{{templ_num}}/ig, value);
        	                    y = y.replace(/{{templ_checked}}/ig, clase == 'active' ? 'checked' : '');
								//console.log("SLL3 " + y);
        	                    $('ul#m' + key).append(y);
        	                    
        		    			break;
        		    		case 'cFecha':
        		    			/* Se pinta slider más abajo */
// 								cadenaFechas += cadenaFechas == '' ? key2 : "," + key2;
        		    			break;
        		    		default:
        		    			mjeDebug("dato no reconocido");
        		    	}
        				
        		    	//mjeInfo("DgtCifras:" + key + " - " + key2 + " = " +value);
        			});
        		});
        		if(arrayFechas.length > 0 ){ 
        			if(getAllUrlParams().fecha == undefined){
        				$(".range-slider").val(arrayFechas[0] + "," + arrayFechas[arrayFechas.length-1]);
        			}
        			
        			$('.range-slider').jRange({
        			    from: arrayFechas[0],
        			    to: arrayFechas[arrayFechas.length-1],
        			    step: 1,
        			    scale:[arrayFechas[0],arrayFechas[arrayFechas.length - 1]],// arrayFechas,
        			    format: '%s',
        			    width: 270,
        			    showLabels: true,
        			    isRange : true, 
        			    ondragend: function(value){
        			    	console.log(value);
        			    	console.log($(".range-slider").val());
        			    	dgtCifrasQuery();
        			    }
        			});
        		}
        		
				var temp = $.trim($('#resultadoPlantilla').html());
				let actualPage = calculoPaginaDGTCifras(numElemPorPagDGTCifras, sortedAndFiltredArray.length);
				let sortedAndFiltredArrayTemp = sortedAndFiltredArray.map((x) => x); /*Creamos una copia porque el splice genera 2 nuevos arrays*/
				let sortedAndFiltredAndPaginatedArray = sortedAndFiltredArrayTemp.splice((actualPage - 1) * numElemPorPagDGTCifras, numElemPorPagDGTCifras)
				/* ******************************************************* *
				**  Pintamos resultados de busqueda filtrados y paginados  *
				** ******************************************************* */
				if(sortedAndFiltredAndPaginatedArray.length == 0){
					$('.resources').append('<li class="results list-group-item"><span class="a-cifras" data-id="006"><h1 class="title-80" alt="No se encontraron resultados"><b>No se encontraron resultados</b></h1></span></li>');
					$("#actualPage").text("0");
				} else {
					$.each(sortedAndFiltredAndPaginatedArray, function (index, obj) {
	                	let recorteTitulo = 95;
	                	let recorteResumen = 200;
	                	let tags = "";
	                	let formatos = "";
	                	let localidades = "";
	                	
	    				$.each(obj.tags.tema.split(","),function(){
	    					let temaActual = tiposTema[this].split("#");
							tags += '<i class="' + temaActual[0] + '"></i>';
	    				});
	                	$.each(obj.tags.formato.split(","),function(){
	                		formatos += '<div class="extension-file ' + this.toLowerCase() + '"><p>' + this.toUpperCase() + '</p></div>';
	                	});
	                	$.each(obj.tags.mapa.split(","),function(){
	                		localidades += '<div class="extension-file ' + this.toLowerCase() + '"><p>' + this.toUpperCase() + '</p></div>';
	                	});
	                	
	                    var x = temp.replace(/{{templ_url}}/ig, "dgt-en-cifras-detalle/?id=" + obj.id);
	                    x = x.replace(/{{templ_id}}/ig, obj.id);
	                    x = x.replace(/{{templ_seccion}}/ig, obj.subseccion);
	                    x = x.replace(/{{templ_titulo}}/ig, obj.titulo.length > recorteTitulo ? obj.titulo.substring(0,recorteTitulo) + "..." : obj.titulo);
	                    x = x.replace(/{{templ_alt_titulo}}/ig, obj.titulo.length > recorteTitulo ? 'alt="' + obj.titulo + '"' : "");
	                    x = x.replace(/{{templ_resumen}}/ig, obj.resumen.length > recorteResumen ? obj.resumen.substring(0,recorteResumen) + "..." : obj.resumen);
	                    x = x.replace(/{{templ_alt_resumen}}/ig, obj.resumen.length > recorteResumen ? 'alt="' + obj.resumen + '"' : "");
	                    x = x.replace(/{{templ_actualizacion}}/ig, obj.fecha_actualizacion);
	                    x = x.replace(/{{templ_extension}}/ig, formatos);
	                    x = x.replace(/{{templ_localidades}}/ig, localidades);
	                    x = x.replace(/{{templ_temas}}/ig, tags);
	                    $('.resources').append(x);
	                });
				}
				dataBundle.mjeDebugBool = false;
			},
			error: function( jqXHR, textStatus, errorThrown ) {
				    mjeDebug( 'Error: ' + textStatus );
			}
		});
	}
	
	if($(".tipo-DGTCifras-Detalle").length){
		$.ajax({
			url: URLCifrasJson,
			dataType : 'json',
			success: function(data){
				let elem = data.filter(function(item){
				    return item.id == getAllUrlParams().id;         
				});
				$(".templ_titulo").html(elem[0].titulo);
				$(".templ_resumen").html(elem[0].resumen);
				$("#TituloDocumento").html(elem[0].titulo_documento);
				
				$("#fecha_creacion .data").html(elem[0].fecha_creacion);
				$("#fecha_actualizacion .data").html(elem[0].fecha_actualizacion);
				$("#idioma .data").html(elem[0].idioma);
				$("#localizacion .data").html(elem[0].localizacion);
				
				let tags = "";
				let formatos = "";
				$.each(elem[0].tags.tema.split(","),function(){
					 tags += '<div class="results badge badge-pill">' + this + '</div>';
				});
				
				$.each(elem[0].tags.categoria.split(","),function(){
					 tags += '<div class="results badge badge-pill">' + this + '</div>';
				});
				
				$.each(elem[0].tags.formato.split(","),function(){
//                     tags += '<div class="results badge badge-pill">' + this + '</div>';
                    formatos += '<div class="extension-file ' + this.toLowerCase() + '"><p>' + this.toUpperCase() + '</p></div>';
				});
				
				$.each(elem[0].tags.fecha.split(","),function(){
					 tags += '<div class="results badge badge-pill">' + this + '</div>';
				});
				$(".tags #tags").html(tags);
				$(".resources .link").prepend(formatos);
				$("#descarga").attr("href",elem[0].url);
				
				
				if(elem[0].otros_recursos){
					$.each(elem[0].otros_recursos,function(index){
						let HTML_TOTAL = "<li class='list-group-item'><p id='TituloDocumento"+index+"'>"+ this.titulo + "</p><div class='link'><div class='extension-file ";
						HTML_TOTAL =  HTML_TOTAL + this.tipo +  "'><p>" +this.tipo.toUpperCase() + "</p></div><div class='vl'></div><a href='";
						HTML_TOTAL =  HTML_TOTAL + this.url +"' id='descarga"+index+  "' class='icon-download' download='' target='_blank'></a></div></li>"
						$(".resources").append(HTML_TOTAL);
					} )
				}
				
				if(elem[0].visor != "" && elem[0].visor != undefined){
					$("#visor").attr("href",rutaVisorCifras + "?id="+ getAllUrlParams().id + "&idVisor=" + elem[0].visor + "&prueba=false");
				} else {
					$("#visor").hide();
				}
			},
			error: function( jqXHR, textStatus, errorThrown ) {
				    mjeDebug( 'Error: ' + textStatus );
			}
		});
	}
	
	if($(".tipo-DGTCifras-Visor").length){
		$(".breadcrumb-item").on("click",function(e){ /* controlamos migas de pan, para volver atras con los parametros puestos*/
			if($(this).attr("id") == "breadcrumb-item-4"){
				e.preventDefault();
				history.back(1);
			}
		});
		$.ajax({
			url: URLCifrasJson,
			dataType : 'json',
			success: function(data){
				let elem = data.filter(function(item){
				    return item.id == getAllUrlParams().id;         
				});
				$(".templ_titulo").html(elem[0].titulo);
				$("#templ_url").attr("href",elem[0].url);
			},
			error: function( jqXHR, textStatus, errorThrown ) {
				    mjeDebug( 'Error: ' + textStatus );
			}
		});
	}
}

function calculoPaginaDGTCifras(numElemPorPagDGTCifras,arrayLength){
	let actualPage = getAllUrlParams().pag != undefined && getAllUrlParams().pag != "" && getAllUrlParams().pag != 'nan' ? getAllUrlParams().pag : 1;
	let limitPage = Math.ceil(arrayLength / numElemPorPagDGTCifras);
	$("#actualPage").html(actualPage);
	$("#limitPage").html(limitPage);
	estadoPaginadoDGTCifras(actualPage,limitPage);
	return actualPage;
}
function estadoPaginadoDGTCifras(actualPage,limitPage){
	if(Number.parseInt(actualPage) > 1){
		$(".pagePrev").removeClass("disabled");
		$(".pageInit").removeClass("disabled");
	}else{
		$(".pagePrev").addClass("disabled");
		$(".pageInit").addClass("disabled");
	}
	if(actualPage < limitPage){
		$(".pageNext").removeClass("disabled");
		$(".pageLast").removeClass("disabled");
	} else{
		$(".pageNext").addClass("disabled");
		$(".pageLast").addClass("disabled");
	}
}

function activaContador(){
	if(contadorNodo == undefined){
		fechaClickNodo = new Date().getTime();
		contadorNodo = setInterval(timerNode, 1000);
	}
}
function timerNode(){
	if(new Date().getTime() >= (fechaClickNodo + 4000)){
		if(!jQuery(".header .navbar-brand #nodo").length){
			jQuery(".header .navbar-brand img").after('<span id="nodo">' + jQuery("body").attr("data-node") + '</span>');
		}
	}
	
}
function desactivaContador(){
	setTimeout(function(){jQuery(".header .navbar-brand #nodo").remove();},1000);
	clearInterval(contadorNodo);
	contadorNodo=undefined;
}

function nodo(){
	$("#header .navbar").mousedown(function(e){activaContador();});
	$("#header .navbar").mouseup(function(e){desactivaContador();});
	$("#header .navbar").mousemove(function(e){desactivaContador();});	// evitamos que se quede activo por fallo en evento anterior de up
	$('body').on('touchstart', function(e){activaContador();});
	$('body').on('touchend', function(e){desactivaContador();});
}

function pestanas(){
	if(getAllUrlParams().tab != undefined){
		$("#"+getAllUrlParams().tab).click();
	};
}

function searchFocus(){
	$("nav .icon-search:first").click(function(){
		setTimeout(function(){
			let elem = $("input[type='search']:first");
			if(elem.parents().hasClass("show")){
				elem.focus();
			}
		},500);
	});
}
function camaras(){
	if($(".contendorCapaCamaras").length){
		$(".contendorCapaCamaras").on("change",".camarasProvincia,.camarasHighway",function(e){
			camarasQuery(e);
		});
		
		$(".contendorCapaCamaras").on("click",".paginadorCamaras a",function(e){
			e.preventDefault();
			camarasQuery(e);
		});
		
		$(".zonaCamaras").on("click",".traffic-link[data-target='#genericModal']",function(){
			let imagenActualizada = $("img",$(this)).attr("data-img") + "?t=" + (new Date()).getTime();
			$("img",$(this)).attr("src",imagenActualizada);
			$("#genericModal .modal-title").text("Cámara de Tráfico");
			$("#genericModal .modal-text").addClass("mb-0 text-center").html('<img class="img-fluid" src="' + imagenActualizada + '" alt="' + $("img",$(this)).attr("alt") + '">').show();
			$("#genericModal").addClass("camaras");
		});
		if(camarasOrderByHighway == undefined){
			$.ajax({
				url: "/.content/.assets/json/camaras.json",
				dataType : 'json',
				success: function(data){
					camaras = data.camaras;
					camarasOrderByHighway = camaras.sort(function(a, b){
					  if (a.carretera < b.carretera) return -1;
					  if (a.carretera > a.carretera) return 1;
					  return 0;
					});
					gestionaCamaras();
				},
				error: function( jqXHR, textStatus, errorThrown ) {
					    mjeDebug( 'Error: ' + textStatus );
				}
			});
		} else{
			gestionaCamaras();
		}
	}
}
function gestionaCamaras(){
	let camarasPorPag = 12;
	let actualizacion = (new Date()).getTime();
	let template = plantillaCamara;	//$.trim($('#movilidadPlantilla').html()); // en offline el CMS lo elimina
	var contadorCamaras = 0;
	
	$(".contenedorloading").show();
	$(".contenedorCamaras").html("");
	
	//var camarasFiltredArray = camaras;
	let camarasFiltredArray = camarasOrderByHighway.slice();
	
	if(getAllUrlParams().prov != undefined && getAllUrlParams().prov != ""){
		camarasFiltredArray= filterCameras(camarasFiltredArray, "prov", getAllUrlParams().prov);
		$("select.camarasProvincia option").removeAttr("selected");
		$("select.camarasProvincia option[data-provid=" + getAllUrlParams().prov + "]").attr("selected","");
	}
	
	selectCamarasCarreteras(camarasFiltredArray);
	if(getAllUrlParams().carr != undefined && getAllUrlParams().carr != ""){
		camarasFiltredArray = filterCameras(camarasFiltredArray, "carr", getAllUrlParams().carr);
		camarasFiltredArray = camarasFiltredArray.sort((a, b) => parseFloat(a.pk) - parseFloat(b.pk));
		if(getAllUrlParams().order == 'desc'){
			camarasFiltredArray.reverse();
		}
	}
	
	let actualPage = calculoPaginaDGTCifras(camarasPorPag,camarasFiltredArray.length);
	let sortedAndFiltredArrayTemp = camarasFiltredArray.slice();
	let sortedAndFiltredAndPaginatedArray = sortedAndFiltredArrayTemp.splice((actualPage - 1) * camarasPorPag, camarasPorPag)
	if(sortedAndFiltredAndPaginatedArray.length){
		$.each(sortedAndFiltredAndPaginatedArray, function (index, obj) {
			if(contadorCamaras ++ < camarasPorPag){
				var provincia;
				provincia = provinciasId[obj.provincia.length < 2 ? "0" + obj.provincia : obj.provincia]["data-nameProv"];
				let pk = replaceAll(obj.pk,"\\.",",");
				let sentido = obj.sentido == "+" ? "Creciente" : (obj.sentido == "-" ? "Decreciente" : "Ambos sentidos");
				var x = template.replace(/{{templ_img_camara}}/ig, obj.imagen);
				x = x.replace(/{{templ_img_camara_timestamp}}/ig, "?t=" + actualizacion);
				x = x.replace(/{{templ_img_camara_alt}}/ig, "Imagen cámara " + obj.carretera + " " + provincia + " Kilómetro " + pk);
				x = x.replace(/{{templ_provincia}}/ig, provincia);
				x = x.replace(/{{templ_carretera}}/ig, obj.carretera);
				x = x.replace(/{{templ_pk}}/ig, pk);
				x = x.replace(/{{templ_sentido}}/ig, sentido);
				$(".contenedorCamaras").append(x);
			}
		});
	} else {
		$(".contenedorCamaras").append($(".contendorCapaCamaras .contenedorMensajeError").html());
	}
	$(".contenedorloading").hide();
}


function selectCamarasCarreteras(camarasFiltredArray){
	let comboCarretera=[];
	$.each(camarasFiltredArray, function (index, elem) {
		if(!comboCarretera.includes( elem.carretera )){
			comboCarretera.push(elem.carretera);
		}
	});
	
	comboCarretera.sort((a, b) => {
		if (a == b) {
			return 0;
		}
		if (a < b) {
			return -1;
		}
		return 1;
	});
	var selectCarretera = '<option value="">Todas</option>';
	$.each(comboCarretera, function (index, elem) {
		let selected = "";
		if(getAllUrlParams().carr != undefined && getAllUrlParams().carr != ""){
			selected = elem == getAllUrlParams().carr.toUpperCase() ? "selected" : "";
		}
		
		selectCarretera += '<option value="' + elem  + '" ' + selected + '>' + elem + '</option>';
	})
	$(".camarasHighway").html(selectCarretera);
}

function filterCameras(array, type, value){
	var arrayTemp = [];
	$.each(array, function (index, obj) {
		if(type == 'prov'){
			if(obj.provincia == value ){
				arrayTemp.push(obj)
			}
		} else if(type == 'carr'){
			if(obj.carretera.toUpperCase() == value.toUpperCase() ){
				arrayTemp.push(obj)
			}
		} else {
			mjeDebug("Error: dato no esperado");
		}
	});
	
	return arrayTemp; 
}

function camarasQuery(e) {
	let provincia = "&prov=" + ($(".contendorCapaCamaras .camarasProvincia option:selected").attr("data-provid") != undefined ? $(".contendorCapaCamaras .camarasProvincia option:selected").attr("data-provid") : '' );
	let carretera = "&carr=" + $(".contendorCapaCamaras .camarasHighway option:selected").val();
	let pagina = "?pag=" + (isNaN(Number.parseInt($("#actualPage").text())) || $("#actualPage").text() == '0' ? 1 : Number.parseInt($("#actualPage").text()));
	let query = "";
	
	var elemPagination = $(e.target).parent();
	if($(e.target).hasClass("page-link")){
		if(elemPagination.hasClass("pageInit")){
			pagina = "?pag=1";
		} else if (elemPagination.hasClass("pagePrev")){
			pagina = "?pag=" + (Number.parseInt($("#actualPage").text()) - 1);
		} else if (elemPagination.hasClass("pageNext")){
			pagina = "?pag=" + (Number.parseInt($("#actualPage").text()) + 1);
		} else { /* pageLast */
			pagina = "?pag=" + Number.parseInt($("#limitPage").text());
		}
	}
	
	if($(e.target).hasClass("camarasProvincia")){
		query = "?pag=1" + provincia;	
	} else if($(e.target).hasClass("camarasHighway")){
		query = "?pag=1" + provincia + carretera;
	} else{
		query = pagina + provincia + carretera;
	}
	
	history.pushState(null, "", query);
	goToAnchor($(".contendorCapaCamaras"));
	gestionaCamaras();
}

function encuentrosDigitales(){
	$(".actualizar").click(function(e){
		e.preventDefault();
		directoEncuentroDigital();
	});
	
	var tiempoRecarga = $(".contenedorPreguntas").attr("data-time");
	var mostrarCapaActualizando = ($(".contenedorPreguntas").attr("data-capaActualizando") === 'true');
	if($(".contenedorPreguntas").hasClass("online") || $(".contenedorPreguntas").hasClass("esperando")){
		const idEncuentroDigital = setInterval(directoEncuentroDigital, tiempoRecarga);
		escribiendo(tiempoRecarga);
		function directoEncuentroDigital() {
			let cargando = '<div class="modal-backdrop-map fade-map fixed-links-backdrop-map show" style="height: ' + $(".contenedorPreguntas").outerHeight() + 'px;">	<div class="result-list"><div class="loading"><p>Actualizando contenidos</p></div></div></div>'
			if(mostrarCapaActualizando)
				$(".contenedorPreguntas").prepend(cargando);
			var url = location.origin + location.pathname;
			$.ajax({
				url: url,
				data: "datos=true",
				dataType : 'html',
				success: function(data){
					$(".estadoDirecto").html($(".estadoDirecto",$(data)).children());
					if(mostrarCapaActualizando)
						$(".contenedorPreguntas").html(cargando);
					
					$(".contenedorPreguntas").html("").append($(".contenedorPreguntas",$(data)).children());
					if($(".estadoDirecto>div").hasClass("online")){
						goToAnchor($(".contenedorPreguntas .pregutas-respuestas:last"));
					}
					else if($(".estadoDirecto>div").hasClass("esperando")) {
						goToAnchor($(".contenedorPreguntas"));
					}
					
					if(!$(".estadoDirecto div").hasClass("online") && !$(".estadoDirecto div").hasClass("esperando")){
						clearInterval(idEncuentroDigital);
						$(".actualizar .refresh").addClass("d-none");
						mjeDebug("Encuentro finalizado");
					}
					$(".modal-backdrop-map.show").addClass("desaparece");
					escribiendo(tiempoRecarga);
				}
			});	
		}
	}
}

function escribiendo(tiempoRecarga){
	if($(".estadoDirecto>div").hasClass("online") ){
		setTimeout(function(){$('.elemEscribiendo').fadeToggle();setTimeout(function(){$('.elemEscribiendo').fadeToggle()},((tiempoRecarga/4)*3)-5)},tiempoRecarga/4)
	}
}

function modalTablas(){
	$("table.table").on("click","[data-target='#genericModal']",function(){
		$("#genericModal .modal-title").text(" ");
		$("#genericModal .modal-text").addClass("mb-0 text-center").html('<img class="img-fluid" src="' + $(this).attr("data-img") + '" alt="' + $(this).attr("data-alt") + '">').show();
		$("#genericModal").addClass("camaras");
	});
}

function ordenaLiCVMU(){
	let clase;
	$("[class*='datosTipo-']").each(function(index){
		clase = "datosTipo-"+ index;
		var result = $('.resultadoCVMU .' + clase + ' ul li').sort(function (a, b) {
			var contentA =parseInt( $(a).data('sort'));
			var contentB =parseInt( $(b).data('sort'));
			return (contentA < contentB) ? -1 : (contentA > contentB) ? 1 : 0;
		});
		let selector;
		$(".resultadoCVMU ." + clase + " ul").html("");
		result.each(function(){
			let lengthUlInit = $("ul:first li", $(".resultadoCVMU ." + clase)).length;
			let lengthUlLast = $("ul:last li", $(".resultadoCVMU ." + clase)).length;
			console.log(clase + ": 1 ul --> " + lengthUlInit);
			console.log(clase + ": 2 ul --> " + lengthUlLast );
			if(lengthUlInit > lengthUlLast){
				selector = "ul:last";
			} else {
				selector = "ul:first";
			}
			elem = $(selector, $(".resultadoCVMU ." + clase));
			elem.append(this);
		});
	});
}

 /*vmp begin*/
selector = "ul:first";
function pintaCvmuImg(marca, modelo){
	datos = "marca=" + marca + "&modelo=" + modelo;
	lanzaPeticionCVMU(datos,true)
}
var datos_cvmu;
var datos_peticion = "";
function lanzaPeticionCVMU(datos,pintarImg,esFormatoNuevo){
	$(".contenedorloading").show();
	if(!pintarImg) {
		borradoDatosCVMU();
	}
	var formatoUl = false;
	datos_peticion = datos;
	$.ajax({
		url: '/peticion/CVMU',
		data: datos,
		dataType : 'json',
		success: function(data){
			datos_cvmu = data;
			if(data.resultado == "OK" || data.mensaje == "Consulta correcta") {
				
				
				/*redireccion de la logica, jose BEGIN*/
				datos_peticion = datos_peticion.split("=")[1].split("&")[1];
				if(datos_peticion == "modelo"){	
					cvmuResultado(data,pintarImg,esFormatoNuevo,tipo="modelo");
					return;
				}else{
					//datos peticion == undefined
					//es una consulta de marca
					cvmuResultado(data,pintarImg,esFormatoNuevo,tipo="marca");
					return;
				}
				/*redireccion de la logica, jose END*/
				
				/*Este otro trozo es lo que hay en f cvmuResultado pero modificado*/
				if(data.hasOwnProperty("respuestaCvmuType") && data.respuestaCvmuType.hasOwnProperty("movilidadUrbana")) {
					if(pintarImg) {
						$("[data-value='" + data.respuestaCvmuType.movilidadUrbana.modelo + "'] .imageVmp").attr("src",data.respuestaCvmuType.movilidadUrbana.imagen)
					} else {
						
						Object.keys(data.respuestaCvmuType.movilidadUrbana).forEach(function(key) {
							let elem = "";
							let indice = "";
							$.each(datosArray,function(index, value){
								if(this.includes(key)){
									indice = this.indexOf(key);
									let selector;
									if(formatoUl){
										selector = "ul:first";
									} else {
										selector = ".col-md-12 .row:first";
									}
									elem = $(selector, $(".resultadoCVMU .datosTipo-" + index));
									return false;
								}
							});
							if(datosTexto.hasOwnProperty(key)){
								titulo = datosTexto[key].titulo										
							} 
							if(elem.length){
								if(formatoUl){
									elem.append('<li data-sort="' + indice + '"><span class="titulo"><b>' + titulo + ': </b></span><span class="dato">' + data.respuestaCvmuType.movilidadUrbana[key] + '</span></li>');
								} else {
									elem.append('<div class="col-6 texto datoRespuesta"><span class="titulo"><b>' + titulo + ':</b></span></div><div class="col-6 resultado datoRespuesta"><span class="dato">' + data.respuestaCvmuType.movilidadUrbana[key] + '</span></div>');
								}	
							}
						});
						ordenaLiCVMU();
						let seleccionados = "";
						let total = $(".vmp .active").length;
						$(".vmp .active .seleccionable").each(function(index){
							seleccionados += $(this).text() + (index === total - 1 ? "":", ");  
						});
						
						$(".resultadoCVMU .seleccion").siblings("h2").html(seleccionados);	//$(".resultadoCVMU .seleccion").html(seleccionados);
						$(".resultadoCVMU .data-seleccion").html(" (" + seleccionados + ")");
						$(".resultadoCVMU").show();
						goToAnchor($(".resultadoCVMU"));
					}
				} else {
					//$(".selectoresCVMU select:disabled:first").append('<option value="">Seleccione</option>');
					let cabeceraImg = "data:image/jpeg;base64,";
					if(esFormatoNuevo){
						$.each(data.respuestaCvmuType,function(index){
							$(".selectoresCVMU .row.d-none:first .vmp").append('<div class="col-sm-6 col-md-3 col-lg-3 "><div class="card on-carousel link"><a href="#" data-value="' + this.movilidadUrbana.modelo + '" class="img-fluid"><span class="img-hover-zoom ampliar"><img data-toggle="modal" data-target="#genericModal" src="/.galleries/Images/vmp/ampliar.png"></span><img class="imageVmp mx-auto d-block" src="' + cabeceraImg + this.movilidadUrbana.imagen + '"><div class="card-body"><p class="card-title seleccionable">' + this.movilidadUrbana.modelo + '</p><p class="card-subtitle marcaSelecionada">' + $(".vmp .active:first").text() + '</p></div></a></div></div>');
						});
						$(".selectoresCVMU .row.d-none:first").removeClass("d-none");
					} else {
						if(data.listado.nombre instanceof Array){
							$.each(data.listado.nombre,function(index){
								$(".selectoresCVMU .row.d-none:first .vmp").append('<div class="col-sm-6 col-md-3 col-lg-3 "><div class="card on-carousel link"><a href="#" data-value="' + this + '" class="img-fluid"><span class="img-hover-zoom ampliar"><img data-toggle="modal" data-target="#genericModal" src="/.galleries/Images/vmp/ampliar.png"></span><img class="imageVmp mx-auto d-block" src=""><div class="card-body"><p class="card-title seleccionable">' + this + '</p><p class="card-subtitle marcaSelecionada">' + $(".vmp .active:first").text() + '</p></div></a></div></div>');
								pintaCvmuImg($(".vmp .active:first").text(), this);
							});	
						} else {
							$(".selectoresCVMU .row.d-none:first .vmp").append('<div class="col-sm-6 col-md-3 col-lg-3 "><div class="card on-carousel link"><a href="#" data-value="' + data.listado.nombre + '" class="img-fluid"><span class="img-hover-zoom ampliar"><img data-toggle="modal" data-target="#genericModal" src="/.galleries/Images/vmp/ampliar.png"></span><img class="imageVmp mx-auto d-block" src=""><div class="card-body"><p class="card-title seleccionable">' + this + '</p><p class="card-subtitle marcaSelecionada">' + $(".vmp .active:first").text() + '</p></div></a></div></div>');
						}
						$(".selectoresCVMU .row.d-none:first").removeClass("d-none");
					}
				}
			} else {
				mostrarErrorCVMU("Error en la respuesta. Por favor intentalo más tarde.");
			}
			$(".contenedorloading").hide();
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			    mjeDebug( 'Error: ' + textStatus );
			    mostrarErrorCVMU("Error al realizar la consulta. Por favor intentalo más tarde.");
			    $(".contenedorloading").hide();
		}
	});
}

function cvmuResultado(data,pintarImg,esFormatoNuevo,tipo){
	//consulta de modelo, puede que venga con un array o solo 1 dato
	//si viene con array son datos repetidos solo cojer el primero
	var formatoUl = false;
	if(tipo == "modelo"){
		if(pintarImg) {
			if(data.respuestaCvmuType.length > 1){
				$("[data-value='" + data.respuestaCvmuType[0].movilidadUrbana.modelo + "'] .imageVmp").attr("src",data.respuestaCvmuType.movilidadUrbana.imagen)
			}
		} else {
			if(data.respuestaCvmuType.length > 1){
				//llega array
				Object.keys(data.respuestaCvmuType[0].movilidadUrbana).forEach(function(key) {
					let elem = "";
					let indice = "";
					$.each(datosArray,function(index, value){
						if(this.includes(key)){
							indice = this.indexOf(key);
							let selector;
							if(formatoUl){
								selector = "ul:first";
							} else {
								selector = ".col-md-12 .row:first";
							}
							elem = $(selector, $(".resultadoCVMU .datosTipo-" + index));
							return false;
						}
					});
					if(datosTexto.hasOwnProperty(key)){
						titulo = datosTexto[key].titulo										
					} 
					if(elem.length){
						if(formatoUl){
							elem.append('<li data-sort="' + indice + '"><span class="titulo"><b>' + titulo + ': </b></span><span class="dato">' + data.respuestaCvmuType[0].movilidadUrbana[key] + '</span></li>');
						} else {
							elem.append('<div class="col-6 texto datoRespuesta"><span class="titulo"><b>' + titulo + ':</b></span></div><div class="col-6 resultado datoRespuesta"><span class="dato">' + data.respuestaCvmuType[0].movilidadUrbana[key] + '</span></div>');
						}	
					}
				});
				ordenaLiCVMU();
				let seleccionados = "";
				let total = $(".vmp .active").length;
				$(".vmp .active .seleccionable").each(function(index){
					seleccionados += $(this).text() + (index === total - 1 ? "":", ");  
				});
				
				$(".resultadoCVMU .seleccion").siblings("h2").html(seleccionados);	//$(".resultadoCVMU .seleccion").html(seleccionados);
				$(".resultadoCVMU .data-seleccion").html(" (" + seleccionados + ")");
				$(".resultadoCVMU").show();
				goToAnchor($(".resultadoCVMU"));
			}else{
				//llega 1
				Object.keys(data.respuestaCvmuType.movilidadUrbana).forEach(function(key) {
					let elem = "";
					let indice = "";
					$.each(datosArray,function(index, value){
						if(this.includes(key)){
							indice = this.indexOf(key);
							let selector;
							if(formatoUl){
								selector = "ul:first";
							} else {
								selector = ".col-md-12 .row:first";
							}
							elem = $(selector, $(".resultadoCVMU .datosTipo-" + index));
							return false;
						}
					});
					if(datosTexto.hasOwnProperty(key)){
						titulo = datosTexto[key].titulo										
					} 
					if(elem.length){
						if(formatoUl){
							elem.append('<li data-sort="' + indice + '"><span class="titulo"><b>' + titulo + ': </b></span><span class="dato">' + data.respuestaCvmuType.movilidadUrbana[key] + '</span></li>');
						} else {
							elem.append('<div class="col-6 texto datoRespuesta"><span class="titulo"><b>' + titulo + ':</b></span></div><div class="col-6 resultado datoRespuesta"><span class="dato">' + data.respuestaCvmuType.movilidadUrbana[key] + '</span></div>');
						}	
					}
				});
				ordenaLiCVMU();
				let seleccionados = "";
				let total = $(".vmp .active").length;
				$(".vmp .active .seleccionable").each(function(index){
					seleccionados += $(this).text() + (index === total - 1 ? "":", ");  
				});
				
				$(".resultadoCVMU .seleccion").siblings("h2").html(seleccionados);	//$(".resultadoCVMU .seleccion").html(seleccionados);
				$(".resultadoCVMU .data-seleccion").html(" (" + seleccionados + ")");
				$(".resultadoCVMU").show();
				goToAnchor($(".resultadoCVMU"));
			}
		}
	}else{
		//es marca, si viene solo 1 dato en la marca hay que meterlo dentro de array
		if(!data.respuestaCvmuType.length){
			data.respuestaCvmuType = [data.respuestaCvmuType];
		}
		if(esFormatoNuevo){
			let cabeceraImg = "data:image/jpeg;base64,"; 
			$.each(data.respuestaCvmuType,function(index){
				$(".selectoresCVMU .row.d-none:first .vmp").append('<div class="col-sm-6 col-md-3 col-lg-3 "><div class="card on-carousel link"><a href="#" data-value="' + this.movilidadUrbana.modelo + '" class="img-fluid"><span class="img-hover-zoom ampliar"><img data-toggle="modal" data-target="#genericModal" src="/.galleries/Images/vmp/ampliar.png"></span><img class="imageVmp mx-auto d-block" src="' + cabeceraImg + this.movilidadUrbana.imagen + '"><div class="card-body"><p class="card-title seleccionable">' + this.movilidadUrbana.modelo + '</p><p class="card-subtitle marcaSelecionada">' + $(".vmp .active:first").text() + '</p></div></a></div></div>');
			});
			$(".selectoresCVMU .row.d-none:first").removeClass("d-none");
		} else {
			if(data.listado.nombre instanceof Array){
				$.each(data.listado.nombre,function(index){
					$(".selectoresCVMU .row.d-none:first .vmp").append('<div class="col-sm-6 col-md-3 col-lg-3 "><div class="card on-carousel link"><a href="#" data-value="' + this + '" class="img-fluid"><span class="img-hover-zoom ampliar"><img data-toggle="modal" data-target="#genericModal" src="/.galleries/Images/vmp/ampliar.png"></span><img class="imageVmp mx-auto d-block" src=""><div class="card-body"><p class="card-title seleccionable">' + this + '</p><p class="card-subtitle marcaSelecionada">' + $(".vmp .active:first").text() + '</p></div></a></div></div>');
					pintaCvmuImg($(".vmp .active:first").text(), this);
				});	
			} else {
				$(".selectoresCVMU .row.d-none:first .vmp").append('<div class="col-sm-6 col-md-3 col-lg-3 "><div class="card on-carousel link"><a href="#" data-value="' + data.listado.nombre + '" class="img-fluid"><span class="img-hover-zoom ampliar"><img data-toggle="modal" data-target="#genericModal" src="/.galleries/Images/vmp/ampliar.png"></span><img class="imageVmp mx-auto d-block" src=""><div class="card-body"><p class="card-title seleccionable">' + this + '</p><p class="card-subtitle marcaSelecionada">' + $(".vmp .active:first").text() + '</p></div></a></div></div>');
			}
			$(".selectoresCVMU .row.d-none:first").removeClass("d-none");
		}
		
	}
	$(".contenedorloading").hide();
}

var marca, modelo;
function cvmu(){
	if($(".tipo-cvmu").length){
		$(".contenedorCVMU").on("click",".ampliar",function(e){
			$("#genericModal .modal-title").text($(".seleccionable",$(this).parent()).text() + ", " + $(".marcaSelecionada",$(this).parent()).text());
			$("#genericModal").addClass("vmp");
			$("#genericModal .modal-text").addClass("mb-0 text-center").html('<img class="img-fluid" src="' + $(this).siblings(".imageVmp").attr("src") + '" alt="' + $("img",$(this)).attr("alt") + '">').show();		
		});
		
		//$(".vmp:first a").click(function (e) {
		$(".vmp").on("click","a",function (e) {
			e.preventDefault();
			$("a",$(this).parents(".vmp")).removeClass("active")
			$(this).addClass("active");
			if($(this).parents(".vmp").hasClass("marca")){
				//$(".selectoresCVMU .row:not(:first)").addClass("d-none");
				$(".selectoresCVMU .row:nth-child(3)").addClass("d-none");
				$(".vmp",$(".selectoresCVMU .row:not(:first)")).html("");
				$(".resultadoCVMU").hide();
			}
			
			//$(".selectoresCVMU .row").not(":first").addClass("d-none");
			//$(".resultado").addClass("d-none");
			
			//hacer ajax query
			let datos = "";
			$(".vmp .active").each(function(){
				if($(this).parents(".vmp").hasClass("marca")){
					datos = "marca=" + $(this).text();
				} else if($(this).parents(".vmp").hasClass("modelo")){
					datos += "&modelo=" + $(".seleccionable",$(this)).text();
				} else if($(this).parents(".vmp").hasClass("version")){
					datos += "&version=" + $(this).text();
					$(".contenedorCVMU .sendCVMU").removeAttr("disabled");
				} else {
					mjeDebug("Error: caso no contemplado");
				}
			});
			
//			if($(".vmp .active").length < 2){
				lanzaPeticionCVMU(datos,false,true);
//			}
		});
		
		$(".contenedorCVMU").on("click",".downloadCVMU",function(e){
			elemNP.addClass("no-print");
			window.print();
			setTimeout(function(){
				elemNP.removeClass("no-print")
			},1000);
		});
		$(".contenedorCVMU").on("click",".error-ico",function(e){
			$(".contenedor-error ").hide();
		});
		
	}
}

function setListenersModelos(){
	//listeners de los modelos
	var div_patinetes = $(".vmp")[1];
	var patinetes = $("a", div_patinetes);
	$(patinetes).click(function (event) {
		event.preventDefault();
		var row_versiones = $(".wrapper.marcas .row")[2];
		$(row_versiones).addClass("d-none");
		$(".resultado").addClass("d-none");
		
		//ajax query
		modelo = $(this).text().trim();
		//var path = "/peticion/CVMU/"+marca+"_"+modelo+"_versiones.json";
		var path = "/peticion/CVMU/"+marca+"_"+modelo+"_version2_resultado.json";
		lanzaPeticion(path, "resultado");

	});	
}

function borradoDatosCVMU(){
	$(".resultadoCVMU").hide();
	$(".resultadoCVMU ul").html("");
	$(".contenedor-error").hide();
	$(".resultadoCVMU .datoRespuesta").remove();
}

function mostrarErrorCVMU(mje){
	borradoDatosCVMU();
	$(".errorCVMU .errorText").html(mje);
	$(".contenedor-error").show();
}
  /*vmp end*/

var gruas_json;
function gruas(){
	if($(".ModuloGruas").length){
		//obtener json matriculas
		getGruasJson();
		
		//listener click busqueda
		$("#buscarMatriculas").click(function(){
			$(".resultadoGruas").addClass("d-none");
			consultaGruas(gruas_json);
		});
		//listener descargar pdf
		$(".resultadoGruas").on("click",".downloadGruas",function(e){
			elemNP.addClass("no-print");
			window.print();
			setTimeout(function(){
				elemNP.removeClass("no-print")
			},1000);
		});
		//listener radio buttons
		$("input[name=tipo]").change(function() {
			var radio_val = this.value;
			//cambiar placeholder del input de texto
			if(radio_val == "CIF"){
				$("input[name=formUser]").attr("placeholder", "A58818501");
			}else{
				$("input[name=formUser]").attr("placeholder", "8568KKB");
			}
		});
	}
}

function getGruasJson(){
	$(".contenedorloading").show();
	$.ajax({
		url: '/.content/.assets/json/gruasM.json',
		data: "",
		dataType : 'json',
		success: function(data){
			gruas_json = data;
			$(".contenedorloading").hide();
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			    mjeDebug( 'Error: ' + textStatus );
			    //mostrarErrorCVMU("Error al realizar la consulta. Por favor intentalo más tarde.");
			    $(".contenedorloading").hide();
		}
	});
}

var tabla_gruas;
function consultaGruas(data){
	if(!data){
		console.log("No se ha podido obtener el json");
		return;
	}
	
	var radio_val = $('input[name=tipo]:checked').val();
	var input_val = $(".consulta_grua input").val().toUpperCase().trim();
	
	var notFound = true;
	if(radio_val == "CIF"){
		// 1-n buscar por cif/nif
		//comprobar input es valido
		if(!isValidCif(input_val)){
			var dni = validateDNI(input_val);
			if(!dni){
				//si no es un cif ni un dni
				$(".resultadoError").removeClass("d-none");
				return;
			}
		}
		
		//guardar coincidencias matriculas
		var matByNif = [];
		$.each(data,function(index, elem){
			if(elem.nif == input_val){
				matByNif.push(elem.M);
			}
		});
		if(matByNif.length == 0){
			console.log("No hay matriculas con ese cif/dni");
			return;
		}
		
		//set datos comunes
		notFound = false;
		var first = matByNif[0];
		var elem = gruas_json[first];
		$(".dato").each(function(){
			//bucle campos html del resultado
			var id_campo = $(this).attr("id");
			Object.keys(elem).forEach(function(key) {
				//bucle los datos del elemento del json
				if(key == id_campo){
					//si el html tiene ese campo y el json tiene ese campo, pintarlo
					$("#" + id_campo).html(elem[key]);
				}
			});
		});
		
		if(matByNif.length == 1){
			//se puede poner un rango de matriculas y separarlas por comas tambien
			//esconder tabla y mostrar campo matricula
			$("#M_tabla").addClass("d-none");
			$("#M").removeClass("d-none");
			if(notFound){
				$(".resultadoError").removeClass("d-none");
			}else{
				$(".resultadoError").addClass("d-none");
				$(".resultadoGruas").removeClass("d-none");
			}
			return;
		}

		//ocultar campo matricula para mostrar la tabla matriculas
		$("#M").addClass("d-none");
		$("#M_texto b").html("Matrículas");
		
		//generacion html de la tabla
		var cont_columna = 0;
		var fila = "";
		var filas = "";
		// modificar esta variable si quieres cambiar el numero de columnas de la tabla
		var numero_columnas = 5; 
		for(var i=0; i<matByNif.length; i++){
			var matricula = matByNif[i];
			if(cont_columna == 0){
				fila += "<tr>";
			}
			var celda = "<td>"+matricula+"</td>";
			fila += celda;
			if(cont_columna == numero_columnas - 1 || i == matByNif.length-1){
				//condicion 1: la fila se ha llenado || condicion 2: se han acabado las matriculas
				if(cont_columna == numero_columnas - 1){
					//todas las celdas estan metidas, cerramos fila
					fila += "</tr>";
				}else if(i == matByNif.length-1 && !(cont_columna == numero_columnas - 1)){
					//si se han acabado todas las matriculas y NO se ha llenado la fila
					//bucle que genera las celdas restante y las inserta
					var restantes = numero_columnas - cont_columna;
					for(var j=0; j<restantes-1; j++){
						fila += "<td></td>";
					}
					fila += "</tr>";
				}
				filas += fila;
				
				
				fila = "";
				cont_columna = -1;
			}
			cont_columna = cont_columna + 1
		}
		
		var table_head = "<tr>";
		for(var i=0; i<numero_columnas; i++){
			table_head += "<th></th>";
		}
		table_head += "</tr>"; 
		
		if(tabla_gruas){
			$('#M_tabla').DataTable().destroy();
			tabla_gruas = undefined;
		}
		
		$("#M_tabla thead").html(table_head);
		$($("#M_tabla").children()[1]).html(filas);
		
		tabla_gruas = $('#M_tabla').DataTable({
			"searching": false,
			"paging": false,
			"info":false,
			"ordering": false,
			"language": {
				"url": '/.content/.assets/json/spanish.json'
			},
			colReorder: false,
			responsive: true
		});
		$("#M_tabla tr").addClass("fondo-transparente");
		$("#M_tabla thead").addClass("invisible");
		$("#M_tabla").removeClass("d-none");
		
	}else{
		// 1-1 buscar por matricula
		var dic_autorizacion = {
			"MDP":"Público mercancías sin limitaciones",
			"MDL":"Público mercancías ligero",
			"MDSL":"Público mercancías superligero",
			"MPC":"Privado mercancías"
		};
		
		var elem = data[input_val];
		if(elem){
			var contador_sindatos = 0;
			//insertar datos en el html
			$(".dato").each(function(){
				//bucle campos html del resultado
				var id_campo = $(this).attr("id");
				$("#" + id_campo).addClass("d-none");
				$("#" + id_campo +"_texto").addClass("d-none");
				Object.keys(elem).forEach(function(key) {
					//bucle los datos del elemento del json
					if(key == id_campo){
						//si el html tiene ese campo y el json tiene ese campo, pintarlo
						$("#" + id_campo).html(elem[key]);
						$("#" + id_campo).removeClass("d-none");
						$("#" + id_campo +"_texto").removeClass("d-none");
						
						if(validateDNI(elem[key])){
							//no se pueden mostrar dnis
							$("#" + id_campo).addClass("d-none");
							$("#" + id_campo +"_texto").addClass("d-none");
						}
						if(elem[key] == ""){
							contador_sindatos += 1;
						}
						if(id_campo == "ca"){
							$("#ca").html(elem[key] + " - " + dic_autorizacion[elem[key]]);
						}
					}
				});
			});
			notFound = false;
			if(contador_sindatos >= 2){
				notFound = true;
			}
			$("#M_texto b").html("Matrícula");
			$("#M").removeClass("d-none");
			$("#M_tabla").addClass("d-none");
		}
	}
	
	if(notFound){
		$(".resultadoError").removeClass("d-none");
	}else{
		$(".resultadoError").addClass("d-none");
		$(".resultadoGruas").removeClass("d-none");
		
	}
}

/* genericModal Close control */
$('#genericModal').on('hidden.bs.modal', function (e) {
	if($(".modal-body iframe").length){
		$(".modal-body iframe").remove();
	}
});

$(function(){
	avisoAlertasHome();
	linkSociales();
	buscador()
	translate();
	audio();
	rrss();
	tasas();
	goTop();
	pagEventosOPunto();
	indiceAnclas();
	cookies();
	lanzaPopOver();
	selectCountryStaticHtml();
	listados();
	DGTCifras();
	nodo();
	pestanas();
	searchFocus();
	camaras();
	encuentrosDigitales();
	modalTablas();
	cvmu();
	BORRAR();
	gruas();
	
// $(".carruselModificar .owl-stage-outer").insertAfter(".carruselModificar
// .owl-nav");//Control posicion elenementos de navegacion para permitir control
// de video
//	
	
	/*
	 * setTimeout(function(){ $(".carousel-item").removeClass("active"); },500);
	 * setTimeout(function(){
	 * $(".carousel-item:first-child").addClass("active"); },700);
	 */
	
});

/* Prueba cifras */
$(function(){
	var jsonData;
	if($(".DGTCifras").length){
		$.ajax({
			url: "/.content/.assets/json/pildoras.json",
			dataType : 'json',
			success: function(data){
				mjeInfo(data);
				jsonData = data;
				$(".DGTCifras .cifras[data-tipo='CifraDinamica']").each(function(){
					var cadena = $(this).attr('data-value').split(".");
					var resultado;
					if(cadena.length == 1){
						resultado = jsonData[cadena[0]];
					} else if (cadena.length = 2){
						resultado = jsonData[cadena[0]][cadena[1]];
					}
					
					$(".cifras-dato1",this).html(resultado.cifra);
					$(".cifras-dato2",this).html(resultado.titulo);
					$(".cifras-dato3",this).html(resultado.fecha);
				});
				
			}
		});
		$(".DGTCifras .cifras[data-tipo='CifraDinamicaMicroStrategy']").each(function(){
			if(typeof jsonPildoras !== 'undefined'){
				var tipoDato = $(this).attr("data-value").split(".");
				
				var pildora = jsonPildoras.result.definition.metrics.filter(function(item){
				    return item.name == tipoDato[0];         
				});
				if(tipoDato[1] == 'max'){
					$(".cifras-dato1",this).html(pildora[0].max);
					$(".cifras-dato3",this).html("max");
				} else if (tipoDato[1] == 'min'){
					$(".cifras-dato1",this).html(pildora[0].min);
					$(".cifras-dato3",this).html("min");
				}
				$(".cifras-dato2",this).html(pildora[0].name);
			} else {
				$(this).hide(); 
				mjeDebug("Detectado fallo conexión Micro")
			}
		});
	}
});
/* FIn Prueba cifras */


function tasas(){
	var jsonData;
	if($(".payment").length){
		$.ajax({
			url: "/.content/.assets/json/tasas.json",
			dataType : 'json',
			success: function(data){
				mjeInfo(data);
				jsonData = data;
				$(".payment [data-tramite], .payment[data-tramite]").each(function(){
					if($(this).attr("data-tipo") == 'curso'){
						$(this).html("Coste del trámite: " + jsonData.curso[$(this).attr("data-tramite").trim()].price + ($(this).attr("data-tramite").trim() != 'gratuito' ? jsonData.currency + jsonData.curso[$(this).attr("data-tramite").trim()].vat : ''));
					} else {
						$(this).html("Coste del trámite: " + jsonData.tasa[$(this).attr("data-tramite").trim()].price + ($(this).attr("data-tramite").trim() != 'gratuito' ? jsonData.currency : ''));
					}
				});
				
			}
		});
	}
}


/*
 * ------------------------------- Pruebas AUDIO subtitulo
 * ------------------------------------------
 */
$(function(){
	if($('#miAudio')[0]!=undefined){
		$('#miAudio')[0].textTracks[0].oncuechange = function() { 
		    var currentCue = this.activeCues[0].text;
		    $('#subtitle').html(currentCue);
		}
	}
});
/*
 * ------------------------------- Fin Pruebas AUDIO subtitulo
 * ------------------------------------------
 */