Struggling with e-Stat API v3.0…
================

## Specifications

  - <https://www.e-stat.go.jp/api/api-info/e-stat-manual3-0>

## APIs

### `getStatsList`

#### CSV

``` r
library(httr)

res_data <- GET(
  "http://api.e-stat.go.jp/", path = "rest/3.0/app/getSimpleStatsData",
  query = list(
    appId      = keyring::key_get("appId", keyring = "estat-api-v3.0"),
    statsDataId = "0003103532",
    cdCat01     = "010800130,010800140",
    sectionHeaderFlg  = 2,
    explanationGetFlg = "Y"
  ))

res <- content(res_data, type = "text/csv;charset=utf-8")
```

    ## Parsed with column specification:
    ## cols(
    ##   tab_code = col_character(),
    ##   表章項目 = col_character(),
    ##   cat01_code = col_character(),
    ##   `品目分類（27年改定）` = col_character(),
    ##   cat02_code = col_character(),
    ##   世帯区分 = col_character(),
    ##   area_code = col_character(),
    ##   地域区分 = col_character(),
    ##   time_code = col_double(),
    ##   `時間軸（月次）` = col_character(),
    ##   unit = col_character(),
    ##   value = col_double(),
    ##   annotation = col_logical()
    ## )

    ## Warning: 604 parsing failures.
    ##  row   col expected actual         file
    ## 1165 value a double      - <raw vector>
    ## 1166 value a double      - <raw vector>
    ## 8843 value a double      - <raw vector>
    ## 8844 value a double      - <raw vector>
    ## 8845 value a double      - <raw vector>
    ## .... ..... ........ ...... ............
    ## See problems(...) for more details.

``` r
knitr::kable(head(res, 20))
```

| tab\_code | 表章項目 | cat01\_code | 品目分類（27年改定） | cat02\_code | 世帯区分            | area\_code | 地域区分 | time\_code | 時間軸（月次）  | unit | value | annotation |
| :-------: | :--- | :---------- | :---------- | :---------- | :-------------- | :--------- | :--- | ---------: | :------- | :--- | ----: | :--------- |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000101 | 2000年1月  | 円    |   323 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000202 | 2000年2月  | 円    |   888 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000303 | 2000年3月  | 円    |   321 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000404 | 2000年4月  | 円    |   271 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000505 | 2000年5月  | 円    |   217 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000606 | 2000年6月  | 円    |   182 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000707 | 2000年7月  | 円    |   156 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000808 | 2000年8月  | 円    |   164 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000000909 | 2000年9月  | 円    |   227 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000001010 | 2000年10月 | 円    |   322 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000001111 | 2000年11月 | 円    |   332 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2000001212 | 2000年12月 | 円    |   406 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2001000101 | 2001年1月  | 円    |   344 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2001000202 | 2001年2月  | 円    |   921 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2001000303 | 2001年3月  | 円    |   337 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2001000404 | 2001年4月  | 円    |   260 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2001000505 | 2001年5月  | 円    |   215 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2001000606 | 2001年6月  | 円    |   190 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2001000707 | 2001年7月  | 円    |   171 | NA         |
|    01     | 金額   | 010800130   | 352 チョコレート  | 03          | 二人以上の世帯（2000年～） | 00000      | 全国   | 2001000808 | 2001年8月  | 円    |   160 | NA         |

#### JSON

``` r
res_data1 <- GET(
  "http://api.e-stat.go.jp/", path = "rest/3.0/app/json/getStatsData",
  query = list(
    appId      = keyring::key_get("appId", keyring = "estat-api-v3.0"),
    statsDataId = "0003103532",
    cdCat01     = "010800130,010800140",
    explanationGetFlg = "Y"
  ))

res1 <- content(res_data1)

res_data2 <- GET(
  "http://api.e-stat.go.jp/", path = "rest/3.0/app/json/getStatsData",
  query = list(
    appId      = keyring::key_get("appId", keyring = "estat-api-v3.0"),
    statsDataId = "0003103532",
    cdCat01     = "010800130,010800140",
    explanationGetFlg = "N"
  ))

res2 <- content(res_data2)

# このへんが違いそう
setdiff(
  names(res1$GET_STATS_DATA$STATISTICAL_DATA$TABLE_INF),
  names(res2$GET_STATS_DATA$STATISTICAL_DATA$TABLE_INF)
)
```

    ## [1] "DESCRIPTION"
