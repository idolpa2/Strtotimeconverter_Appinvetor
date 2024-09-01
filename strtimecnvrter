package com.saisab.strtotimeconverter;

import android.app.Activity;
import android.content.Context;
import com.google.appinventor.components.annotations.*;
import com.google.appinventor.components.common.ComponentCategory;
import com.google.appinventor.components.runtime.AndroidNonvisibleComponent;
import com.google.appinventor.components.runtime.ComponentContainer;
import java.time.Instant;
import java.time.ZoneId;
import java.time.ZonedDateTime;
import java.time.format.DateTimeFormatter;

@DesignerComponent(
    version = 1,
    description = "A simple extension for converting ISO 8601 datetime strings to formatted date-time strings with customizable format",
    category = ComponentCategory.EXTENSION,
    nonVisible = true,
    iconName = "https://www.saisab.com/assets/images/og.jpg"
)
@SimpleObject(external = true)
public class Strtotimeconverter extends AndroidNonvisibleComponent {

    private Context context;
    private Activity activity;

    public Strtotimeconverter(ComponentContainer container) {
        super(container.$form());
        this.activity = container.$context();
        this.context = container.$context();
    }

    @SimpleFunction(description = "Convert ISO 8601 datetime string to formatted datetime string with customizable format. Optionally specify the time zone.")
    public String ConvertIsoToFormattedDate(String isoDateTime, String formatPattern, String timeZone) {
        try {
            // Convert ISO 8601 string to Instant
            Instant instant = Instant.parse(isoDateTime);
            
            // Default time zone is UTC
            ZoneId zoneId = (timeZone == null || timeZone.isEmpty()) ? ZoneId.of("UTC") : ZoneId.of(timeZone);
            
            // Convert Instant to ZonedDateTime in the desired time zone
            ZonedDateTime dateTime = instant.atZone(zoneId);
            
            // Define a formatter with the desired output format from input pattern
            DateTimeFormatter formatter = DateTimeFormatter.ofPattern(formatPattern);
            
            // Format the ZonedDateTime object to string
            return dateTime.format(formatter);
        } catch (Exception e) {
            // Handle the error and return an error message
            return "Error converting ISO 8601 string: " + e.getMessage();
        }
    }
}
