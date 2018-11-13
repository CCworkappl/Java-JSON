# Java-JSON



import com.google.gson.*;

import java.io.FileNotFoundException;
import java.io.FileReader;

public class Json {
    public static void main(String args[]) {


        //创建JSON解析器
        JsonParser parser = new JsonParser();

        try {
            //创建JsonObject对象
            JsonObject object = (JsonObject) parser.parse(new FileReader("C:\\Users\\kyle\\IdeaProjects\\test\\src\\test.json"));

            System.out.println("message=" + object.get("message").getAsString());

            JsonObject data = object.get("data").getAsJsonObject();//创建data对象

            System.out.println("ip=" + "'"+data.get("ip").getAsString()+"'");
            System.out.println("city=" + data.get("city").getAsString());

            JsonObject subobject = data.get("weather").getAsJsonObject();//weather对象在data对象内，在data对象基础上创建weather对象
            System.out.println("weather:{");
            System.out.println("dat_condition=" + subobject.get("dat_condition").getAsString());
            System.out.println("dat_low_temperature=" + subobject.get("dat_low_temperature").getAsInt());
            System.out.println("wind_direction=" +subobject.get("wind_direction").getAsString());
            System.out.println("high_temperature=" + subobject.get("high_temperature").getAsInt());
            System.out.println("low_temperature=" + subobject.get("low_temperature").getAsInt());
            System.out.println("current_time=" + subobject.get("current_time").getAsInt());
            System.out.println("tomorrow_weather_icon_id=" + subobject.get("tomorrow_weather_icon_id").getAsInt());
            System.out.println("dat_high_temperature=" + subobject.get("dat_high_temperature").getAsInt());
            System.out.println("}");

            System.out.println("forecast_list[");
            JsonArray array1 = subobject.get("forecast_list").getAsJsonArray();//得到forecast_list的数组
            for (int i = 0;i<array1.size();i++){
                System.out.println("============================");
                JsonObject forecast_list = array1.get(i).getAsJsonObject();//创建forecast_list的对象
                System.out.println("wind_direction="+forecast_list.get("wind_direction").getAsString());
                System.out.println("high_temperature=" + forecast_list.get("high_temperature").getAsInt());
                System.out.println("weather_icon_id=" + forecast_list.get("weather_icon_id").getAsInt());
                System.out.println("condition="+forecast_list.get("condition").getAsString());
                System.out.println("date=" + forecast_list.get("date").getAsString());
                System.out.println("wind_level=" + forecast_list.get("wind_level").getAsString());
                System.out.println("low_temperature=" + forecast_list.get("low_temperature").getAsInt());
            }
            System.out.println("]");
            System.out.println("wind_level=" + subobject.get("wind_level").getAsInt());


            System.out.println("hourly_forecast[");
            JsonArray array2 = subobject.get("hourly_forecast").getAsJsonArray();//得到forecast_list的数组
            for (int i = 0;i<array2.size();i++){
                System.out.println("============================");
                JsonObject forecast_list1 = array2.get(i).getAsJsonObject();//创建forecast_list的对象
                System.out.println("temperature="+forecast_list1.get("temperature").getAsInt());
                System.out.println("hour="+forecast_list1.get("hour").getAsInt());
                System.out.println("wind_direction="+forecast_list1.get("wind_direction").getAsString());
                System.out.println("weather_icon_id="+forecast_list1.get("weather_icon_id").getAsInt());
                System.out.println("wind_level="+forecast_list1.get("wind_level").getAsInt());
                System.out.println("condition="+forecast_list1.get("condition").getAsString());
            }
            System.out.println("]");
            System.out.println("current_temperature=" + subobject.get("current_temperature").getAsInt());
            System.out.println("weather_icon_id=" + subobject.get("weather_icon_id").getAsInt());
            System.out.println("quality_level=" + subobject.get("quality_level").getAsString());
            System.out.println("tomorrow_high_temperature=" + subobject.get("tomorrow_high_temperature").getAsInt());
            System.out.println("tomorrow_aqi=" + subobject.get("tomorrow_aqi").getAsInt());

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (JsonIOException e) {
            e.printStackTrace();
        } catch (JsonSyntaxException e) {
            e.printStackTrace();
        } catch (IllegalStateException e) {
            e.printStackTrace();
        }catch (NullPointerException e){
            e.printStackTrace();
        }
    }
}

