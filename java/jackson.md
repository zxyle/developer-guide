## 注解

- @JsonProperty("private") 指定json文件字段
- @JsonIgnore 忽略
- @JsonFormat(pattern = "yyyy-MM-dd HH:mm:ss", timezone = "GMT+8")
- @JsonIgnoreProperties(value = {"createTime", "updateTime", "version", "deleted"})
- @JsonComponent