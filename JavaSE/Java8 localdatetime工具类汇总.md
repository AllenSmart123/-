# 1.LocalDate转Date
```java
LocalDate nowLocalDate = LocalDate.now();
Date date = Date.from(localDate.atStartOfDay(ZoneOffset.ofHours(8)).toInstant());
```
# 2.LocalDateTime转Date
```java
LocalDateTime localDateTime = LocalDateTime.now();
Date date = Date.from(localDateTime.atZone(ZoneOffset.ofHours(8)).toInstant());
```
# 3.Date转LocalDateTime(LocalDate)
```java
Date date =newDate();
LocalDateTime localDateTime = date.toInstant().atZone(ZoneOffset.ofHours(8)).toLocalDateTime();
LocalDate localDate = date.toInstant().atZone(ZoneOffset.ofHours(8)).toLocalDate();
```
# 4.LocalDate转时间戳
```java
LocalDate localDate = LocalDate.now();
longtimestamp = localDate.atStartOfDay(ZoneOffset.ofHours(8)).toInstant().toEpochMilli();
```
# 5.LocalDateTime转时间戳
```java
LocalDateTime localDateTime = LocalDateTime.now();
longtimestamp = localDateTime.toInstant(ZoneOffset.ofHours(8)).toEpochMilli();
```
# 6.时间戳转LocalDateTime(LocalDate)
```java
longtimestamp = System.currentTimeMillis();
LocalDate localDate = Instant.ofEpochMilli(timestamp).atZone(ZoneOffset.ofHours(8)).toLocalDate();
LocalDateTime localDateTime = Instant.ofEpochMilli(timestamp).atZone(ZoneOffset.ofHours(8)).toLocalDateTime();
```
# 7.LocalDateTime获取毫秒数
```java
//获取秒数
Long second = LocalDateTime.now().toEpochSecond(ZoneOffset.of("+8"));
//获取毫秒数
Long milliSecond = LocalDateTime.now().toInstant(ZoneOffset.of("+8")).toEpochMilli();
```
# 8.LocalDateTime与String互转
```java
//时间转字符串格式化
 DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyyMMddHHmmssSSS");
 String dateTime = LocalDateTime.now(ZoneOffset.of("+8")).format(formatter);
 
//字符串转时间
String dateTimeStr = "2018-07-28 14:11:15";
DateTimeFormatter df = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
LocalDateTime dateTime = LocalDateTime.parse(dateTimeStr, df);
```
# 9.Date与LocalDateTime互转
```java
//将java.util.Date 转换为java8 的java.time.LocalDateTime,默认时区为东8区
    public static LocalDateTime dateConvertToLocalDateTime(Date date) {
        return date.toInstant().atOffset(ZoneOffset.of("+8")).toLocalDateTime();
    }
 
   
    //将java8 的 java.time.LocalDateTime 转换为 java.util.Date，默认时区为东8区
    public static Date localDateTimeConvertToDate(LocalDateTime localDateTime) {
        return Date.from(localDateTime.toInstant(ZoneOffset.of("+8")));
    }
 
 
    /**
     * 测试转换是否正确
     */
    @Test
    public void testDateConvertToLocalDateTime() {
        Date date = DateUtils.parseDate("2018-08-01 21:22:22", DateUtils.DATE_YMDHMS);
        LocalDateTime localDateTime = DateUtils.dateConvertToLocalDateTime(date);
        Long localDateTimeSecond = localDateTime.toEpochSecond(ZoneOffset.of("+8"));
        Long dateSecond = date.toInstant().atOffset(ZoneOffset.of("+8")).toEpochSecond();
        Assert.assertTrue(dateSecond.equals(localDateTimeSecond));

    }
 ```
 # 10 获取当天最大和最小时间
 ```java
 String todayStart = LocalDateTime.of(date, LocalTime.MIN).format(DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss"));
String todayEnd = LocalDateTime.of(date, LocalTime.MAX).format(DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss")); 
 ```
