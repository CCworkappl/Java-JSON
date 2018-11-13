# Java-JSON
import com.google.gson.*;

import java.io.FileNotFoundException;
import java.io.FileReader;

public class ReadJSON {
    public static void main(String args[]) {
        //创建JSON解析器
        JsonParser parser = new JsonParser();
        try{
            //创建JsonObject对象
            JsonObject object = (JsonObject) parser.parse(new FileReader("C:\\Users\\kyle\\IdeaProjects\\test\\src\\test.json"));
            System.out.println("cat="+object.get("cat").getAsString());
            System.out.println("pop="+object.get("pop").getAsBoolean());

            //得到为json数组
            JsonArray array = object.get("language").getAsJsonArray();
            for (int i = 0;i<array.size();i++){
                System.out.println("----------------------");
                JsonObject subobject = array.get(i).getAsJsonObject();
                System.out.println("id="+subobject.get("id").getAsInt());
                System.out.println("ide="+subobject.get("ide").getAsString());
                System.out.println("name="+subobject.get("name").getAsString());

            }

        }catch (FileNotFoundException e){
              e.printStackTrace();
        }catch (JsonIOException e){
            e.printStackTrace();


        }catch(JsonSyntaxException e){
            e.printStackTrace();
        }

    }
}
＃test.json
{
  "message": "success",
  "data": {
    "ip": "",
    "weather": {
      "dat_condition": "\u6674",
      "dat_low_temperature": 17,
      "wind_direction": "\u4e1c\u5317\u98ce",
      "high_temperature": 23,
      "low_temperature": 18,
      "current_time": 1542076734,
      "tomorrow_weather_icon_id": "0",
      "dat_high_temperature": 24,
      "forecast_list": [
        {
          "wind_direction": "\u4e1c\u5317\u98ce",
          "high_temperature": "23",
          "weather_icon_id": "0",
          "condition": "\u6674",
          "date": "2018-11-13",
          "wind_level": "4-5",
          "low_temperature": "18"
        }
      ],
      "wind_level": 2,
      "dat_weather_icon_id": "0",
      "update_time": "2018-11-13 10:30:08",
      "day_condition": "\u6674",
      "night_condition": "\u6674",
      "tomorrow_quality_level": "\u4f18",
      "moji_city_id": 1665,
      "city_name": "\u53a6\u95e8",
      "aqi": 23,
      "tomorrow_condition": "\u6674",
      "current_condition": "\u591a\u4e91",
      "tomorrow_low_temperature": 17,
      "hourly_forecast": [
        {
          "temperature": "19",
          "hour": "9",
          "wind_direction": "NE",
          "weather_icon_id": "2",
          "wind_level": "24",
          "condition": "\u9634"
        }

      ],
      "current_temperature": 20,
      "weather_icon_id": "1",
      "quality_level": "\u4f18",
      "tomorrow_high_temperature": 24,
      "tomorrow_aqi": 36
    },
    "city": "\u53a6\u95e8"
  }
}
