<template>
  <section class="primary">
    <div class="primary_info">
      <h2 class="primary_title">
        <span class="primary_subtitle">Discover</span> Rare Collection of
        Digital Art <span class="primary_subtitle">and</span> NFT
      </h2>
      <div class="primary_description">
        Digital marketplace for crypto assets and non fungible tokens (NFT)
      </div>
      <div class="primary_icons">
        <ul class="primary_icons_list">
          <li v-for="img in imgs" :key="img"><img :src="img" alt="artwork" /></li>
        </ul>
        <div class="primary_icons_description">
          <div class="description_number">100+</div>
          <div class="description_text">The best designers</div>
        </div>
      </div>
      <a class="primary_details">Discover latest Artworks</a>
    </div>
    <div class="primary_gallery">
      <div class="primary_card">
        <div class="primary_card_source">
          <div class="source_collection">Troy Ape collection</div>
          <div class="source_author">@tonyti</div>
        </div>
        <img :src="monkeyImg" alt="card" class="primary_card_img" />
        <div class="primary_card_info">
          <div class="info_time">
            <div class="time_main"><base-timer></base-timer></div>
            <div class="time_additional">Remaining time</div>
          </div>
          <div class="info_cost">
            <div class="cost_main">23.09 ETH</div>
            <div class="cost_additional">Highest bid</div>
          </div>
        </div>
      </div>
    </div>
    <ul class="primary_statistics_list">
      <li
        class="primary_statistics_list_item"
        v-for="listItem in listItems"
        :key="listItem"
      >
        <div class="statistics_main_info">
          {{ listItem.main }}
        </div>
        <div class="statistics_additional_info">
          {{ listItem.additional }}
        </div>
      </li>
    </ul>
  </section>
</template>

<script setup>
import { reactive } from "vue";
import Img1 from "@/assets/images/main1.png";
import Img2 from "@/assets/images/main2.png";
import Img3 from "@/assets/images/main3.png";
import monkeyImg from "@/assets/images/monkey.png";
const imgs = reactive([Img1, Img2, Img3]);
const listItems = [
  {
    main: "10.1k+",
    additional: "Art Work",
  },
  {
    main: "1.1M",
    additional: "Artists",
  },
  {
    main: "38k",
    additional: "Sales",
  },
];
</script>

<style scoped lang="scss">
$grayPrint: rgba(255, 255, 255, 0.6);

.primary {
  margin-top: 150px;
  padding: 20px 7% 10%;
  background-color: #131313;
  font-family: "Arial";
  color: #ffffff;
  display: flex;
  flex-wrap: wrap;
  gap: 45px;
  justify-content: center;

  @media (min-width: 800px) {
    margin-top: 177px;
  }

  @media (min-width: 922px) {
    justify-content: space-between;
  }

  @media (min-width: 1024px) {
    padding: 20px 10% 10%;
  }

  @media (min-width: 1440px) {
    padding: 0 10% 159px;
    margin-top: 204px;
  }

  &_info {
    display: flex;
    flex-direction: column;
    gap: 22px;
    max-width: 400px;

    @media (min-width: 716px) {
      max-width: 267px;
    }

    @media (min-width: 1440px) {
      max-width: 383px;
      gap: 43px;
    }
  }

  &_title {
    font-weight: 700;
    font-size: 42px;
    line-height: 55px;
    letter-spacing: 0.015em;
    margin: 0;

    @media (min-width: 716px) {
      font-size: 39px;
      line-height: 48px;
    }

    @media (min-width: 768px) {
      font-size: 42px;
    }

    @media (min-width: 922px) {
      font-size: 48px;
    }

    @media (min-width: 1440px) {
      font-size: 55px;
      line-height: 63px;
    }
  }

  &_subtitle {
    font-weight: 400;
    font-size: 42px;
    line-height: 49px;

    @media (min-width: 768px) {
      font-size: 40px;
    }

    @media (min-width: 1440px) {
      font-size: 55px;
      line-height: 63px;
    }
  }

  &_description {
    font-weight: 400;
    font-size: 22px;
    line-height: 33px;

    @media (min-width: 716px) {
      font-size: 20px;
      line-height: 26px;
    }

    @media (min-width: 1440px) {
      font-size: 22px;
      line-height: 33px;
    }
  }

  &_icons {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;

    @media (min-width: 1440px) {
      gap: 13px;
      justify-content: flex-start;
    }

    &_list {
      display: flex;
      justify-content: space-between;
      list-style-type: none;
      margin-block-start: 0;
      margin-block-end: 0;
      padding-inline-start: 0;
      pointer-events: none;
    }

    &_description {
      display: flex;
      flex-direction: column;
      justify-content: space-around;

      .description_number {
        font-weight: 700;
        font-size: 22px;
        line-height: 33px;
      }

      .description_text {
        font-weight: 400;
        font-size: 14px;
        line-height: 17px;
        color: $grayPrint;

        @media (min-width: 1440px) {
          font-size: 18px;
          line-height: 27px;
        }
      }
    }
  }

  &_details {
    position: relative;
    font-weight: 700;
    font-size: 22px;
    line-height: 38%;
    cursor: pointer;

    @media (min-width: 768px) {
      font-size: 20px;
      line-height: 124%;
    }

    @media (min-width: 1440px) {
      font-size: 24px;
      line-height: 36px;
      padding-top: 43px;
    }
  }

  &_details::before {
    content: "";
    display: inline-block;
    position: absolute;
    top: 28px;
    width: 63px;
    height: 2px;
    background-color: #5ba300;

    @media (min-width: 768px) {
      font-size: 20px;
      line-height: 124%;
      top: 34px;
    }

    @media (min-width: 922px) {
      top: 39px;
    }

    @media (min-width: 1440px) {
      top: 95px;
    }
  }

  &_details::after {
    content: url(@/assets/icons/arrow-right.svg);
    display: none;
    position: absolute;

    @media (min-width: 1440px) {
      display: block;
      top: 47px;
      left: 291px;
    }
  }

  &_gallery {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    z-index: 2;
  }

  &_card {
    background-color: #131313;
    border: 1px solid #5ba300;
    padding: 27px 18px;
    display: flex;
    flex-direction: column;
    gap: 14px;

    @media (min-width: 1440px) {
      padding: 31px 26px 35px;
    }

    &_img {
      width: 260px;
      height: auto;
      pointer-events: none;

      @media (min-width: 1440px) {
        width: 394px;
        height: 477px;
      }
    }

    &_source {
      display: flex;
      justify-content: space-between;

      .source_collection {
        font-weight: 700;
        font-size: 17px;
        line-height: 30px;

        @media (min-width: 1440px) {
          font-size: 20px;
          line-height: 30px;
        }
      }

      .source_author {
        font-weight: 400;
        font-size: 16px;
        line-height: 27px;
        color: $grayPrint;

        @media (min-width: 1440px) {
          font-size: 18px;
          line-height: 28px;
        }
      }
    }

    &_info {
      display: flex;
      justify-content: space-between;

      .info_time,
      .info_cost {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        gap: 4px;

        .time_main,
        .cost_main {
          font-weight: 400;
          font-size: 17px;
          line-height: 33px;

          @media (min-width: 1440px) {
            font-size: 22px;
            line-height: 33px;
          }
        }

        .time_additional,
        .cost_additional {
          font-weight: 400;
          font-size: 16px;
          line-height: 27px;
          color: $grayPrint;

          @media (min-width: 1440px) {
            font-size: 18px;
            line-height: 27px;
          }
        }
      }
    }
  }

  &_card::after {
    content: "";
    display: inline-block;
    top: 13px;
    left: 10px;
    position: absolute;
    width: 298px;
    height: 493px;
    border: 1px solid #5ba300;
    z-index: -1;

    @media (min-width: 716px) {
      top: 14px;
      left: 15px;
    }

    @media (min-width: 1440px) {
      width: 448px;
      height: 667px;
      top: 23px;
      left: 25px;
    }
  }

  &_statistics_list {
    display: flex;
    justify-content: space-between;
    gap: 32px;
    margin: 0;
    padding: 0;

    @media (min-width: 922px) {
      flex-direction: column;
      justify-content: flex-end;
    }

    @media (min-width: 1440px) {
      gap: 36px;
    }

    &_item {
      display: flex;
      flex-direction: column;
      gap: 9px;

      @media (min-width: 1440px) {
        gap: 5px;
      }

      .statistics_main_info {
        font-weight: 700;
        font-size: 30px;
        line-height: 29px;

        @media (min-width: 1440px) {
          font-size: 36px;
          line-height: 41px;
        }
      }

      .statistics_additional_info {
        font-weight: 700;
        font-size: 17px;
        line-height: 26px;
        color: $grayPrint;

        @media (min-width: 1440px) {
          font-size: 20px;
          line-height: 30px;
        }
      }
    }
  }
}
</style>
