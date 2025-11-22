$('document').ready(function () {
	//Inclusion de enlace de politica de cookies
	 var linkElement = $(".cc-text");
	 var content = "Utilizamos cookies para mejorar tu experiencia en nuestra web. Al continuar navegando por la web aceptas nuestras <a href='/contenido/politica-de-cookies/'>políticas de cookies.</a>";
     linkElement.html(content);
	 linkElement.find('a').css({
      'color': 'white' // Cambia el color a blanco
      //'text-decoration': 'none' // Quita el subrayado
   });
	
    if ($(".timeline").length) {
        if ($(window).width() < 700) {
            $(".timeline").parent().addClass('vertical')
            $().timelinr({
                arrowKeys: 'true',
                orientation: 'vertical'
            });



        } else {
            $(".timeline").parent().addClass('horizontal')
            $().timelinr({

                arrowKeys: 'true',
                orientation: 'horizontal'
            });

        }
    }

    $(".timeline a").click(function () {
        setTimeout(function () {
            $(".timeline ul li").removeClass("selected2");
            $(".timeline ul li a[class='selected']").parent().addClass("selected2");
        }, 100);

    });




    initialize();
    let $searcher = $('.main-searcher, .map-searcher');
    $searcher.autoComplete({
        resolverSettings: {
            url: '../assets/vendors/autocomplete/data.json'
        }
    });

    $('.table-complex .table').DataTable({
        "language": {
            "url": '/.content/.assets/json/spanish.json'
        },
        "lengthMenu": [10, 25, 50, 75, 100],
        responsive: true
    });


	var ttipo = $('.table-filter .table').attr("ptype");	
    $('.table-filter .table').DataTable({
        //buscador oculto por estilos TODO
        "searching": true,
        "paging": false,
		"order":  [1,'desc'],
        "columnDefs": [
            { "width": "31%", "targets": 0 },
            { "width": "86px", "targets": -2 },
            { className: "text-center", "targets": -1 },
			{  "targets": 1, 
				render: function (data, type, full) 
				{
					if (type == 'display') {
						var dtStart = new Date(parseInt(data));
						var dtStartWrapper = moment(dtStart);						
						return dtStartWrapper.lang("es").format('DD MMMM YYYY');
					} else {
						return data;
					}									
				}
			},
			{  "targets": parseInt(ttipo), 
				render: function (data, type, full) 
				{
					if (type == 'display') {
						var sdates = data.split("-");
						var dtStart = new Date(parseInt(sdates[0]));
						var dtStartWrapper = moment(dtStart);
						var dtEnd = new Date(parseInt(sdates[1]));
						var dtEndWrapper = moment(dtEnd);						
						return dtStartWrapper.lang("es").format('DD MMMM YYYY') + "-" + dtEndWrapper.lang("es").format('DD MMMM YYYY');
					} else {
						return data;
					}									
				}
			}
        ],
        "language": {
            "url": '/.content/.assets/json/spanish.json'
        },
        responsive: true,
        initComplete: function () {
            // var arrayTables = [".table-data-type", ".table-data-state"];
            for (var i = 0; i < arrayColumns.length; i++) {
                this.api().columns(arrayColumns[i]).every(function () {
                    var column = this;


                    var select = $('<select><option value=""></option></select>')
                        .appendTo(".select" + arrayColumns[i])
                        .on('change', function () {
                            var val = $.fn.dataTable.util.escapeRegex(
                                $(this).val()
                            );

                            column
                                .search(val ? '^' + val + '$' : '', true, false)
                                .draw();
                        });

                    column.data().unique().sort().each(function (d, j) {
                        select.addClass("custom-select");
                        // $(".custom-select").wrap("<div class='filter'></div>");

                        select.append('<option>' + d + '</option>')
                    });
                });
            }
            ;
        }

    });

    $(".table-basic .table").DataTable({
        "searching": false,

        "paging": false,
        "ordering": false,
        "info": false,
        "language": {
            "url": '/.content/.assets/json/spanish.json'
        },
        responsive: true
    });

    let $flipdown = $('.flipdown');

    if ($flipdown.length) {
        $flipdown.each(function () {
            new FlipDown(parseInt(($(this).attr('data-init'))) / 1000, $(this).attr('id'),
            		{
            			headings: ["Días", "Horas", "Minutos", "Segundos"]
            		}
            	)           	
                .start()
                .ifEnded(() => {
                    console.log('The countdown has ended!');
                });
        });
    }

    let $calendar = $('#calendar');

    if ($calendar.length) {
        let calendar = new FullCalendar.Calendar($calendar[0], {
            headerToolbar: {
                left: 'today',
                center: 'title',
                right: 'prev,next' // will normally be on the right. if RTL, will be on the left
            },
            dayHeaderFormat: { weekday: 'long' },
            bootstrapFontAwesome: false,
            locale: 'es',
            moreLinkText: 'eventos',
            dayMaxEvents: true,
            views: {
                dayGridMonth: { // name of view
                    titleFormat: { year: 'numeric', month: 'long' },
                }
            },
            //titleFormat: { year: 'numeric', month: 'long' },
            themeSystem: 'bootstrap',
            eventClick: function (info) {
                mjeDebug('a event has been clicked!');
                mjeDebug('Event: ' + info.event.title);
                mjeDebug('Coordinates: ' + info.jsEvent.pageX + ',' + info.jsEvent.pageY);
                mjeDebug('View: ' + info.view.type);
            },
            dateClick: function (info) {
                mjeDebug('Clicked on: ' + info.dateStr);
                mjeDebug('Coordinates: ' + info.jsEvent.pageX + ',' + info.jsEvent.pageY);
                mjeDebug('Current view: ' + info.view.type);
                mjeDebug('Date: ' + info.dateStr);
                //                mjeDebug('Resource ID: ' + info.resource.id);
                modalEvent(info.dateStr);
                //                $('#modalDayDetail').modal('show');
            },

            eventContent: function (eventInfo) {
                return {
                    html: '<div class="fc-event-main-frame"><div class="fc-event-title-container"><div class="fc-event-title fc-sticky">' +
                        eventInfo.event.title + '</div></div></div>'
                }
            },

            events: calendarEvents,
            eventBackgroundColor: '#fff',
            eventTextColor: '#333',
            eventBorderColor: '#0057A6',
        });
        calendar.render();
    }



    let $carouselImageVideo = $('.image-video.carousel .owl-carousel');
    let $carouselActionsImageVideo = $('.actions.image-video.carousel .owl-carousel');
    let $carouselText = $('.carousel-text .owl-carousel');
    let $carouselDigitText = $('.digit.text .owl-carousel');
    let $carouselDigit = $('.digits .owl-carousel');
    let $carousel = $('.hero .owl-carousel');
    let $carousel2Digit = $('.digits2 .owl-carousel');
    let $carousel3Digit = $('.digits3 .owl-carousel');
    let $carousel4Digit = $('.digits4 .owl-carousel');
    let $carousel5Digit = $('.digits5 .owl-carousel');
    let $carousel1Digit = $('.digits1 .owl-carousel');

    $carousel.owlCarousel({
	autoplay: true,
autoplayTimeout:10000,
        //autoWidth: true, // TODO explore this option to perform mobile
        items: 1,
        loop: true,
        dots: true, // no aparecen a no ser que haya 4 elementos
    });

    $carouselActionsImageVideo.owlCarousel({
        items: 2,
        loop: false,
        margin: 30,
        merge: true,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        responsive: {
            576: {
                nav: true
            },
            992: {
                items: 4,
                nav: true
            }
        }
    });

    $carouselImageVideo.owlCarousel({
        items: 4,
        loop: false,
        margin: 30,
        merge: true,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        responsive: {
            576: {
                items: 1,
                mergeFit: true,
                nav: true
            }
        }
    });

    $carouselText.owlCarousel({
        items: 1,
        loop: false,
        margin: 30,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        nav: true,
        dots: false
    });

    $carouselDigitText.owlCarousel({
        items: 1,
        loop: false,
        margin: 30,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        nav: true,
        dots: true
    });

    $carouselDigit.owlCarousel({
        items: 1,
        loop: false,
        margin: 30,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        nav: true,
        dots: true,
        responsive: {
            768: {
                items: 3,
                margin: 0,
                mergeFit: true,
            }
        }
    });

    $carousel2Digit.owlCarousel({
        items: 1,
        loop: false,
        margin: 30,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        responsive: {
            768: {
                items: 2,
                nav: true,

                dots: true,
                margin: 0,
                mergeFit: true,
            }
        }
    });
    $carousel3Digit.owlCarousel({
        items: 1,
        loop: false,
        margin: 30,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        responsive: {
            768: {
                items: 3,
                nav: true,

                dots: true,
                margin: 0,
                mergeFit: true,
            }
        }
    });


    $carousel4Digit.owlCarousel({
        items: 1,
        loop: false,
        margin: 30,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        responsive: {
            768: {
                items: 4,
                nav: true,

                dots: true,
                margin: 0,
                mergeFit: true,
            }
        }
    });
    $carousel5Digit.owlCarousel({
        items: 1,
        loop: false,
        margin: 30,
        navText: ["<span class='icon-chevron'></span>", "<span class='icon-chevron'></span>"],
        responsiveClass: true,
        responsive: {
            768: {
                items: 5,
                nav: true,

                dots: true,
                margin: 0,
                mergeFit: true,
            }
        }
    });


    $carousel1Digit.owlCarousel({
        items: 1,
        loop: false,
        margin: 30,
        navText: ["<a id='prev'></a>", "<a id='next'></a>"],
        responsiveClass: true,
        nav: false,
        responsive: {
            768: {
                items: 1,
                margin: 0,
                mergeFit: true,
            }
        }
    });



    $("#next-arrow").on("click", function () { $("#next").click() });
    $("#prev-arrow").on("click", function () { $("#prev").click() });

    $("[data-mostrar-mas]").on("click", function (e) {
        var link = $(this);

        e.preventDefault();
        var expander = $(this).siblings(".expander");
		if(expander.length == 0){	//Para casos especificos que no tengan la estructura normal
			expander = $(this).parents().siblings(".expander");
		}
        expander.slideToggle("fast", function () {
            if ($(this).is(":visible")) {

                link.text(link.attr("data-close"));
                link.css("color", "#666666");
                link.attr('aria-expanded', 'false');
                link.removeClass().addClass(link.attr("data-close-class"));

                // let style = window.getComputedStyle(link.get(0), ':before');



            } else {
                if (link.hasClass("responsive")) {
                    link.text(link.attr("data-open"));
                    link.css({ "color": "#666666" });
                    link.removeClass().addClass(link.attr("data-open-class"));
                } else {
                    link.text(link.attr("data-open"));
                    link.css({ "color": "#0057a6" });
                    link.removeClass().addClass(link.attr("data-open-class"));

                }
            }
        });
    });

    if ($(".tipo-DGTCifras-Visor").length) {
        spanEnd();
    }

});
function spanEnd() {
    var END = $("#calendar-end");
    if (!END.length) {
        setTimeout(spanEnd, 200);
    } else {

        $(".num-registros .label-1").html(END.html());

    }
}

//function googleTranslateElementInit() {
//    new google.translate.TranslateElement({ pageLanguage: 'de' }, 'google_translate_element');
//}

function customTranslate() {
//    setTimeout(function () {
//        $(".pre-header .select.dropdown .dropdown-menu a span").on("click", function () {
//            var lang = $(this).text();
//            // var value = $("#google_translate_element .goog-te-combo").val(lang);
//            //value.click();
//            var event;
//
//            var classic = jQuery('#google_translate_element .goog-te-combo');
//            for (var i = 0; i < classic.length; i++) {
//                event = classic[i];
//            }
//
//            if (document.getElementById('google_translate_element') != null) {
//                if (classic.length != 0) {
//
//                    event.value = "";
//                    event.value = "catalán";
//                    GLTFireEvent(event, 'change', lang);
//
//                }
//            }
//            // $("#google_translate_element .goog-te-combo option[value=" + lang + "]").click();
//
//        });
//        /* $('#google_translate_element .goog-te-combo').on('change', function () {
//            try {
//                if (document.createEvent) {
//                    var event = document.createEvent("HTMLEvents");
//                    event.initEvent(lang_dest, true, true);
//                    lang_pair.dispatchEvent(event)
//                } else {
//                    var event = document.createEventObject();
//                    lang_pair.fireEvent('on' + lang_dest, event)
//                }
//            } catch (e) { }
//        }); */
//    }, 2000);

}

function acordionFixed() {
    var s = $(".titleCamino");
    if($(".titleCamino").length){
	    var pos = s.position();
	    var sideBarSantiago = $(".sidebar.reverse");
	    $(sideBarSantiago).scroll(function () {
	        var windowpos = $(sideBarSantiago).scrollTop();
	
	
	        if (windowpos >= pos.top) {
	            s.removeClass("p-initial");
	            s.addClass("stick");
	        } else {
	            s.removeClass("stick");
	
	        }
	    });
	
	    $(window).scroll(function () {
	        s.removeClass("stick");
	        s.addClass("p-initial");
	
	    });
    }
}

function GLTFireEvent(lang_pair, lang_dest, lang_custom) {
    try {


        if (document.createEvent) {
            lang_pair.val(lang_custom);
            var event = document.createEvent("HTMLEvents");
            event.initEvent(lang_dest, true, true);
            lang_pair.dispatchEvent(event);
        } else {
            var event = document.createEventObject();
            lang_pair.fireEvent('on' + lang_dest, event)
        }
    } catch (e) { }
}

/* function googleTranslate() {
    setTimeout(function () {
        $("#google_translate_element .goog-te-combo").on("click", function () {
            console.log("select lang");
            /*  var lang = $(this).text();
             console.log("langGoogle" + lang); 
            var selected = $("#google_translate_element .goog-te-combo option:selected").text();
            console.log("selected_google : " + selected);
        });
    }, 1000);

}

function translate() {


} */


function oneCalendar(selector) {
    var plus_5_days = new Date;
    plus_5_days.setDate(plus_5_days.getDate() - 5);
    pickmeup.defaults.locales['es'] = {
        days: ['Domingo', 'Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado'],
        daysShort: ['Dom', 'Lun', 'Mar', 'Mie', 'Jue', 'Vie', 'Sab'],
        daysMin: ['D', 'L', 'M', 'X', 'J', 'V', 'S'],
        months: ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'],
        monthsShort: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun', 'Jul', 'Ago', 'Sep', 'Oct', 'Nov', 'Dic']
    };
    pickmeup(selector, {
        flat: true,
        title_format: 'B Y',
        locale: 'es',
        format: 'Y-m-d',
        mode: 'range',
        prev: '<span class=\'icon-chevron\'></span>',
        next: '<span class=\'icon-chevron\'></span>',
        render: function (date) {
            if (date.getDate() === plus_5_days.getDate()) {
                return { class_name: 'highlight' };
            }
        }
    });
}






function twoCalendar(selector) {

    //var arrayDates = [new Date(2021, 03, 16), new Date(2021, 03, 15), new Date(2021, 03, 03)];
    pickmeup.defaults.locales['es'] = {
        days: ['Domingo', 'Lunes', 'Martes', 'Miércoles', 'Jueves', 'Viernes', 'Sábado'],
        daysShort: ['Dom', 'Lun', 'Mar', 'Mie', 'Jue', 'Vie', 'Sab'],
        daysMin: ['D', 'L', 'M', 'X', 'J', 'V', 'S'],
        months: ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'],
        monthsShort: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun', 'Jul', 'Ago', 'Sep', 'Oct', 'Nov', 'Dic']
    };
    var calendars = $(selector);



    $(calendars).each(function (index, elem) {
        //alert(index);
        if (elem.className == "two-calendars3" || elem.className == "d-lg-none d-md-none d-sm-block one-calendar3") {
            var description = $(selector)[index].attributes["data-fechas"].value;
            if (description) {
                var elements = description.split("|");
            }
            if (elem.className == "d-lg-none d-md-none d-sm-block one-calendar3") {
                var numCalendars = 1;
            }
            else {
                numCalendars = 2;
            }

            var dateToDisplay = new Date(elements[0]);
            console.log(dateToDisplay.toLocaleDateString());


            //dateToDisplay.setDate(dateToDisplay.getMonth() - 6);
            //console.log(dateToDisplay.toLocaleDateString());

            pickmeup(elem, {
                flat: true,
                locale: 'es',

                select_year: false,
                date: dateToDisplay,
                select_month: false,
                select_day: true,
                mode: 'single',
                min: dateToDisplay.setDate(dateToDisplay.getMonth() - 1),
                max: dateToDisplay,
                prev: '<img src="/.content/.assets/img/1x1.png">',
                next: '<img src="/.content/.assets/img/1x1.png">',

                render: function (date) {
                    /* for (var i = 0; i < arrayDates.length; i++) {
                        if (date.getTime() === arrayDates[i].getTime()) {
                            return { class_name: 'highlight' };
                        }
                    } */

                    for (var i = 0; i < elements.length; i++) {
                        var elementDate = new Date(elements[i]);
                        if (date.getTime() === elementDate.getTime()) {
                            return { class_name: 'highlight' };
                        }
                    }
                    /* 
                                    elements.forEach(elem => function (index, elem) {
                                        //alert(new Date(elem))
                                        elementDate = new Date(elem);
                                        if (date.getTime() === elementDate.getTime()) {
                                            return { class_name: 'highlight' };
                                        }
                                    }) */
                    return { disabled: true };

                },
                calendars: numCalendars
            });
        } else {
            var plus_5_days = new Date;
            plus_5_days.setDate(plus_5_days.getDate() - 5);

            pickmeup(selector, {
                flat: true,
                title_format: 'B Y',
                locale: 'es',
                format: 'Y-m-d',
                mode: 'range',
                prev: '<span class=\'icon-chevron\'></span>',
                next: '<span class=\'icon-chevron\'></span>',
                render: function (date) {
                    if (date.getDate() === plus_5_days.getDate()) {
                        return { class_name: 'highlight' };
                    }
                },
                calendars: 2
            });

        }
    })
    // pickmeup(selector).set_date(plus_5_days.getDate() - 5);
}


function socialLinks() {
    $('.fixed-links').on('click', function () {
        $('.fixed-links-backdrop').toggleClass('show');
    });

    $('.fixed-links-backdrop').on('click', function () {
        $('.fixed-links').trigger('click');
    });

    $('#collapseFixedLinks li').after().on('click', function () {
        $('.fixed-links').trigger('click');
    });
}

function addTitleSubmenu() {
    let $linkChild = $('.header .navbar-nav .nav-link.dropdown-toggle, .header .navbar-nav .childs > a');

    $.each($linkChild, function (index, element) {
        const text = $(element).text();

        $('<span class=\"nav-title\">' + text + '</span>').insertAfter($(element).siblings().find('> .back'));
    });
}


function menuSidebar() {
    let $toggleButton = $('.filter-group .icon-filter');
    let test = $(".filter-group .btn.icon-filter").attr("aria-controls");

    console.log(test);
    let $sidebar = $('.filter-group .sidebar');
    let $backdrop = $('.filter-backdrop');

    $toggleButton.add($backdrop).on('click', function () {
        toggleMenuMobile($toggleButton, $sidebar);
    });
}

function toggleMenuMobile($toggleButton, $sidebar) {

    var ariaControls = $toggleButton.attr("aria-controls");
    if (ariaControls == "sidebarFilter2") {
        $(".column-map.sidebar.open").addClass("checks-cifras");
    }
    $toggleButton.attr('aria-expanded',
        $toggleButton.attr('aria-expanded') === 'false'
    );
    $sidebar.toggleClass('open');

    $('body').toggleClass('overflow-hidden');

}

function mapSidebar() {
    let $toggleButton = $('.map .search');
    let $sidebar = $('.map .sidebar');
    let $close = $sidebar.find('.close');

    $toggleButton.add($close).on('click', function () {
        $sidebar.toggleClass('open');
    });
}

function menuMobile() {
    let isMobile = function () {
        return $(window).width() < 1200;
    };
    $('.header .navbar-backdrop, .header .navbar-toggler').on('click', function () {
        if (isMobile()) {
            let $toggleButton = $('.header .navbar-toggler');
            let $navbarCollapse = $(this).siblings('.navbar-collapse');
            let $searcher = $('.header').find('.toggle-search[aria-expanded=true]');

            if ($searcher.length) {
                $searcher.trigger('click');
                setTimeout(
                    function () {
                        toggleMenuMobile($toggleButton, $navbarCollapse);
                    }, 350);
            } else {
                toggleMenuMobile($toggleButton, $navbarCollapse);
            }

            $navbarCollapse.removeClass('overflow-hidden');
            $navbarCollapse.find('.dropdown-menu').removeClass('d-block overflow-hidden show');
        }
    });

    $('.header .childs > .dropdown-item').on('click', function () {
        if (isMobile()) {
            let $childs = $(this).parent();

            $childs.find('> .dropdown-menu').addClass('show');

            $childs.parent().scrollTop(0).addClass('d-block overflow-hidden');
        }
    });

    $('.header .navbar-nav').find('.back').on('click', function () {
        if (isMobile()) {
            let $dropMenu = $(this).parent();

            $dropMenu.removeClass('d-block overflow-hidden show');
            $dropMenu.parent().parent().removeClass('overflow-hidden').addClass('show');

            if ($dropMenu.parent().hasClass('nav-item')) {
                $dropMenu.parent().parent().parent().removeClass('overflow-hidden');
            }
        }
    });

    $('.header .dropdown-toggle').on('click', function (e) {
        if (isMobile()) {
            let $navbarCollapse = $(this).parent().parent().parent();

            $navbarCollapse.scrollTop(0);
            $navbarCollapse.addClass('overflow-hidden');
        }
    });
}

function resetDesktopMenuHeight() {
    $('.header .navbar-nav').find('.dropdown:not(.secondary) > .dropdown-menu').removeAttr('style');
}

function setDesktopMenuHeight() {
    let $dropdownMenuFirstLevel = $('.header .navbar-nav').find('.dropdown:not(.secondary) > .dropdown-menu');

    $dropdownMenuFirstLevel.each(function () {
        let maxHeight = 0;
        let $elements = $(this).find('.dropdown-menu').addBack($(this));

        $elements.each(function () {
            let $element = $(this);
            $element.addClass('d-block height-auto');

            if ($element.height() > maxHeight)
                maxHeight = $element.height();
        });

        $(this).height(maxHeight);

        $elements.removeClass('d-block height-auto');
    });
}

function checkOpenMenuOnPreHeader() {
    let $items = $('.pre-header .navbar-nav').find('.show');
    if ($items.length) {
        $items.find('.dropdown-toggle').click();
    }
}

function menuDesktop() {
    let isMobile = function () {
        return $(window).width() < 1200;
    };
    let $expanded = $('.header .childs > .dropdown-item, .header .dropdown-toggle');

    $expanded.on('mouseover', function () {
        if (!isMobile()) {
            let $element = $(this);
            checkOpenMenuOnPreHeader();

            $element.attr('aria-expanded', 'true');

            $element.parent().on('mouseleave', function () {
                $element.attr('aria-expanded', 'false');
                $element.siblings().removeClass('show');
                $element.parent().removeClass('show');
            });
        }
    });

    if (!isMobile()) {
        setDesktopMenuHeight();
    }

    $(window).on('resize', function () {
        if (!isMobile())
            setDesktopMenuHeight();
        else
            resetDesktopMenuHeight();
    });
}

// select
function setActive($selects, $item) {
    const $input = $selects.find('.dropdown-toggle');

    let text;

    $item && !$item.hasClass('active') ?
        text = setAria($selects, $item) :
        text = $selects.find('.active').text();

    $input.find('span:nth-child(2)').text(text.trim().substring(2));
    $input.find('span:nth-child(1)').text(text.trim().substring(0,2).trim());
}

function activeFilter() {
    $('.column-map').on('click', ' .cifras-map .cifras-row', function () {
        console.log($(this));
        if ($(this).hasClass("clicked")) {
            var id = $(this).children().attr("id");
            $('.checks-responsive input[id=' + id + ']').prop('checked', false);
            $(this).removeClass("clicked");
            $(this).children().removeClass("active")
        }
        else {
            var id = $(this).children().attr("id");
            $('.checks-responsive input[id=' + id + ']')[0].checked = true;
            $(this).addClass("clicked");
            $(this).children().addClass("active")
        }
    }
    );

    $('.checks-responsive input').on('click', function () {
        var id = $(this).attr("id");
        var elementDesktop = $('.column-map .cifras-map .cifras-row p[id=' + id + ']').parent();

        if ($(this)[0].checked == true) {

            $(elementDesktop).addClass("clicked");
            $(elementDesktop).children("i").addClass("active");
        }
        else {
            $(elementDesktop).parent().removeClass("active");
            $(elementDesktop).children("i").removeClass("active");
            $(elementDesktop).removeClass("clicked");
        }
    }
    );



}


function setAria($selects, $item) {
    $selects.find('.active').removeClass('active').removeAttr('aria-selected');
    $item.addClass('active').attr('aria-selected', true);

    return $item.text();
}

function selectedDropdown() {
    const SELECTOR = '.dropdown.select';
    const $selects = $(SELECTOR);
    const $items = $selects.find('.dropdown-item');

    setActive($selects);

    $items.on('click', function () {
        setActive($(this).closest(SELECTOR), $(this));
    });
}

function selectTabs() {
    $('.tabs .custom-select').on('change', function () {
        $(this).next('nav').find('a').eq($(this).val()).tab('show');
    });
}

function fontResize() {
    let $plus = $('.actions .increase');
    let $less = $('.actions .decrease');
    let $reset = $('.actions .reset');
    let $target = $('.container .text-to-resize');
    let reset = $target.css('font-size');

    $plus.on('click', function () {
        $target.css({
            fontSize: parseFloat($target.css('font-size')) + 2
        })
    });

    $less.on('click', function () {
        $target.css({
            fontSize: parseFloat($target.css('font-size')) - 2
        })
    });

    $reset.on('click', function () {
        $target.css({
            fontSize: reset
        })
    });
}

function homeDGTCifras() {

    var checkobxClicked = false;

   /* $('.row.cifras .cifras-filters .icon-cifras').hover(

        function () {

            if ($('.row.cifras .description-filters').hasClass("d-none")) {
                $('.row.cifras .default-filters').addClass("d-none");
                $('.row.cifras .description-filters').removeClass("d-none").html($(this).siblings("div").html());
            } else {
                $('.row.cifras .description-filters').addClass("d-none");
                $('.row.cifras .default-filters').removeClass("d-none");

            }
        }
    );*/

    $('.row.cifras .cifras-filters .icon-cifras input').change(function () {


        checkobxClicked = true;

    });

    $('.row.cifras .cifras-filters .icon-cifras').click(
        function (e) {
            // e.preventDefault();
           /* if (e.target.type == "checkbox") {
                if ($(window).width() < 977) {
                    if (($(this).hasClass("box-shadow-div-desktop"))) {
                        $(this).removeClass("box-shadow-div-desktop");
                    }
                    else {
                        $(this).addClass("box-shadow-div-desktop");
                    }
                }
                //al apretar checkbox , añadir clase boxshadow nueva (solo desktop)
                // $(".multi-collapse.collapse.show").removeClass("show");
            }
            else {*/
            if ($(window).width() < 977) {
            	$(".icon-cifras input").prop('checked', false);
        		$($(".icon-cifras.box-shadow-div-mobile").attr("data-target")).toggle("toggle")
                $(".icon-cifras").removeClass("box-shadow-div-mobile");
                $(this).addClass("box-shadow-div-mobile");
                $($(this).attr("data-target")).toggle("toggle");
                $("input", this).prop('checked', true);
            } else {
                if ($("input", this).prop('checked') == false) {
                	homeDGTCifrasReset();
                    $("input", this).prop('checked', true);
                    $(this).addClass("box-shadow-div-desktop");
                    $('.row.cifras .default-filters').addClass("d-none");
                    $('.row.cifras .description-filters').removeClass("d-none").html($(this).siblings("div").html());
                    $('.row.cifras .button-filters').removeClass("d-none");
                }
                else {
                	homeDGTCifrasReset();
                }

              /*  if ($(this).hasClass("box-shadow-div-desktop")) {
                    $(this).removeClass("box-shadow-div-desktop");

                }
                else {
                    $(this).addClass("box-shadow-div-desktop");
                }*/
                }
           /* }*/
        }
    );
}

function homeDGTCifrasReset(){
	/*Solo se permite un único filtro acceso*/
	elems =  $('.row.cifras .cifras-filters .icon-cifras');
	elems.removeClass("box-shadow-div-desktop");
	elems.removeClass("box-shadow-div-mobile");
	$("input", elems).prop('checked', false);
	$('.row.cifras .description-filters').addClass("d-none");
	$('.row.cifras .button-filters').addClass("d-none");
    $('.row.cifras .default-filters').removeClass("d-none");
}



function initialize() {
    oneCalendar('.one-calendar');
    oneCalendar('.one-calendar2');
    //oneCalendar('.one-calendar3');
    oneCalendar('.no-results');
    twoCalendar('.two-calendars');
    twoCalendar('.one-calendar3');
    twoCalendar('.two-calendars3');
    // linkSociales();
    fontResize();
    socialLinks();
    menuDesktop();
    menuMobile();
    addTitleSubmenu();
    selectedDropdown();
    activeFilter();
    selectTabs();
    /* googleTranslate();
    translate(); */
    customTranslate();
    menuSidebar();
    mapSidebar();
    homeDGTCifras();
	acordionFixed();
}

















/***********************************************************************/


