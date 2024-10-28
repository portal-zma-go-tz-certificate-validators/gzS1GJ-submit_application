// Niue Online Registry Registry System V2- JS
//Author: Andrew Estolonio
function fnDatePicker(id)
{
    $(id).datepicker({
        changeMonth: true,
        changeYear: true,
        dateFormat: "dd/mm/yy",
        yearRange: "-22:+15"
    });
    $(id).datepicker("option", "showAnim", "clip");
}

function fnDatePickerFull(id) {
    $(id).datepicker({
        changeMonth: true,
        changeYear: true,
        dateFormat: "dd MM yy",
        yearRange: "-22:+15"
    });
    $(id).datepicker("option", "showAnim", "clip");
}


function PopulateKeelLaid()
{
    const monthNames = ["JAN", "FEB", "MAR", "APR", "MAY", "JUN",
        "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"
    ];
    var qntYears = 69;
    var selectYear = $("#year");
    var selectMonth = $("#month");
    var selectDay = $("#day");
    var TempDay = $("#TempDay");
    var currentYear = new Date().getFullYear();

    for (var y = 0; y < qntYears; y++) {
        let date = new Date(currentYear);
        var yearElem = document.createElement("option");
        yearElem.value = currentYear
        yearElem.textContent = currentYear;
        selectYear.append(yearElem);
        currentYear--;
    }

    for (var m = 0; m < 12; m++) {
        let monthNum = new Date(currentYear, m).getMonth();
        let month = monthNames[monthNum];
        var monthElem = document.createElement("option");

        monthElem.value = monthNum;
        monthElem.textContent = month;
        selectMonth.append(monthElem);
    }

    var d = new Date();
    var month = d.getMonth();
    var year = d.getFullYear();
    var day = d.getDate();

    //selectYear.val(year);
    //selectYear.on("change", AdjustDays);
    //selectMonth.val(month);
    //selectMonth.on("change", AdjustDays);

    //AdjustDays();
    //selectDay.val(day)

    for (var d = 1; d <= 31; d++) {
        var dayElem = document.createElement("option");
        dayElem.value = d;
        dayElem.textContent = d;
        selectDay.append(dayElem);
        //TempDay.append(dayElem);
    }

    for (var d = 1; d <= 31; d++) {
        var dayElem2 = document.createElement("option");
        dayElem2.value = d;
        dayElem2.textContent = d;
        TempDay.append(dayElem2);
    }
    
    function AdjustDays() {

        var year = selectYear.val();
        var month = parseInt(selectMonth.val()) + 1;

        if (isNaN(month)) {
            month = 1;
        }


        //alert(month);
        TempDay.empty();

        //get the last day, so the number of days in that month
        var days = new Date(year, month, 0).getDate();

        //lets create the days of that month
        var _day = document.createElement("option");
        _day.value = d;
        _day.textContent = d;
        TempDay.append(_day);
        _day.value = "Day";
        _day.textContent = "--Day--";

        for (var d = 1; d <= days; d++) {
            var dayElem = document.createElement("option");
            dayElem.value = d;
            dayElem.textContent = d;
            TempDay.append(dayElem);
        }

        var ArrDay = [];
        var ArrTempDay = [];

        $("#day > option").each(function () {
            ArrDay.push(this.value);
        });

        $("#TempDay > option").each(function () {
            ArrTempDay.push(this.value);
        });

 
        var res = ArrDay.filter(function (n) { return !this.has(n) }, new Set(ArrTempDay));

        var res2 = ArrTempDay.filter(function (n) { return !this.has(n) }, new Set(ArrDay));

     

        if (res != '') {

            for (var index = 0; index < res.length; index++) {
                $("#day option[value='" + res[index] + "']").remove();
            }
        }

        if (res2 != '') {

            
            var x = document.getElementById("day");

            for (var index1 = 0; index1 < res2.length; index1++) {
                    
                var opt = document.createElement("option");
                opt.text = res2[index1];
                opt.value = res2[index1];
                x.add(opt);
            }
        }

    }
}

function ValidateKeelLaid(KeelLaid) {

    if (KeelLaid != '') {

        var keel = KeelLaid;
        var res = keel.split("/");

        var day = document.getElementById("day");
        var month = document.getElementById("month");
        var year = document.getElementById("year");


        if (res.length > 0) {
            //day.value = res[0];

            if (!isNaN(res[0])) {
                if (res[0] >= 10) {
                    day.value = res[0];
                }
                else {
                    //res[0] = res[0].substring(1);
                    if (res[0] === "0") {
                        day.value = "Day";
                    }
                    else {
                        //day.value = res[0].toString().substring(1);
                        if (res[0] == '01' || res[0] == '02' || res[0] == '03' || res[0] == '04' || res[0] == '05' || res[0] == '06' || res[0] == '07' || res[0] == '08' || res[0] == '09') {
                            day.value = res[0].toString().substring(1);
                        }
                        else {
                            day.value = res[0];
                        }
                        //alert(res[0].toString().substring(1));
                    }
                }
            }
            else {
                day.value = res[0];

            }

            if (!isNaN(res[1])) {
                if (res[1] >= 10) {
                    month.value = res[1] - 1;
                }
                else {


                    //res[1] = res[1].substring(1);


                    if (res[1] === "0") {
                        month.value = "Month";
                    }
                    else {
                        month.value = res[1] - 1;
                    }
                }
            }
            else {
                month.value = res[1];
            }



            year.value = res[2];
        }
    }
}

jQuery(document).ready(function ($) {

    // Disable scroll when focused on a number input.
    $('form').on('focus', 'input[type=number]', function (e) {
        $(this).on('wheel', function (e) {
            e.preventDefault();
        });
    });

    // Restore scroll on number inputs.
    $('form').on('blur', 'input[type=number]', function (e) {
        $(this).off('wheel');
    });

    // Disable up and down keys.
    $('form').on('keydown', 'input[type=number]', function (e) {
        if (e.which == 38 || e.which == 40)
            e.preventDefault();
    });

});


function getParameterByName(name, url) {
    if (!url) url = window.location.href;
    name = name.replace(/[\[\]]/g, "\\$&");
    var regex = new RegExp("[?&]" + name + "(=([^&#]*)|&|#|$)"),
        results = regex.exec(url);
    if (!results) return null;
    if (!results[2]) return '';
    return decodeURIComponent(results[2].replace(/\+/g, " "));
}


function validateFloatKeyPress(el, evt) {
    var charCode = (evt.which) ? evt.which : event.keyCode;
    var number = el.value.split('.');
    if (charCode != 46 && charCode > 31 && (charCode < 48 || charCode > 57)) {
        return false;
    }

    if (number.length > 1 && charCode == 46) {
        return false;
    }

    var caratPos = getSelectionStart(el);
    var dotPos = el.value.indexOf(".");
    if (caratPos > dotPos && dotPos > -1 && (number[1].length > 1)) {
        return false;
    }
    return true;
}

function getSelectionStart(o) {
    if (o.createTextRange) {
        var r = document.selection.createRange().duplicate()
        r.moveEnd('character', o.value.length)
        if (r.text == '') return o.value.length
        return o.value.lastIndexOf(r.text)
    } else return o.selectionStart
}

function MaxGtNt(ID, ERR_ID, SUBMIT_ID)
{
    $("#" + ID).keyup(function () {
        var Val = this.value;

        if (Val > 500000) {
            $("#" + ERR_ID).show();
            $("#" + SUBMIT_ID).attr("disabled", true);
        }
        else
        {
            $("#" + ERR_ID).hide();
            $("#" + SUBMIT_ID).attr("disabled", false);
        }
    });

    //non keyup
    var _val = $("#" + ID).val();
    if (_val > 500000) {
        $("#" + ERR_ID).show();
        $("#" + SUBMIT_ID).attr("disabled", true);
    }
    else {
        $("#" + ERR_ID).hide();
        $("#" + SUBMIT_ID).attr("disabled", false);
    }
}


function GoToManager(id) {

    $.ajax({
        type: "GET",
        url: "/Niue/PostReference",
        dataType: "json",
        data: { id: 0, fr: 2, manager_id: id },
        contentType: "application/json; charset=utf-8",
        success: function (returndata) {
            if (returndata.ok)
                window.location = returndata.newurl;
            else
                window.alert(returndata.message);
        }

    });
}
