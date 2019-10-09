<template>
  <div class="contacts">
    <div class="container-fluid">
      <h1 class="contacts__title">Contacts</h1>
      <div class="row align-items-center">
        <div class="col-xs-12 col-lg-4 contacts__item">
          <h2 class="contacts__caption"><span>GMS</span> Headquarters</h2>
          <ul class="contacts__list">
            <li class="contacts__text">Global Message Services Ukraine LLC</li>
            <li class="contacts__text">Bundesstrasse 5 | 3rd Floor</li>
            <li class="contacts__text">6300 Zug</li>
            <li class="contacts__text">Switzerland</li>
          </ul>
          <a class="contacts__tel" href="tel:+41415446200">+41 41 544 62 00</a>
        </div>
        <div class="col-xs-12 col-lg-4 contacts__item">
          <p class="contacts__text">Email</p>
          <a class="contacts__link" href="mailto:info@gms-worldwide.com">info@gms-worldwide.com</a>
          <p class="contacts__text">Send Message</p>
          <a class="contacts__link" href="tel:+41415446200">viber us</a>
          <p class="contacts__text">Send form</p>
          <a class="contacts__link" href="#">Contact us</a>
        </div>
        <div class="col-xs-12 col-lg-4 contacts__item">
          <h2 class="contacts__caption">Technical support <span>24/7</span></h2>
          <p class="contacts__text contacts__info">GMS understands that it can be hard to follow all new technologies. We regularly provide for all our clients educational trainings to make your operator`s business earn more and better though our best practices.</p>
          <a class="contacts__tel" href="tel:+41415446206">+41 41 544 62 06</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'contacts'
}
</script>


<style lang="scss" scoped>

.contacts {
  background: #ffffff;
  padding: 60px 60px 100px 60px;
  &__title {
    font-weight: 300;
    font-size: 50px;
    line-height: 48px;
    color: #333333;
    margin-bottom: 46px;
  }
  &__caption {
    font-weight: 300;
    font-size: 34px;
    line-height: 48px;
    color: #2e2e2e;
    margin-bottom: 41px;
    span {
      color: #3db565;
    }
  }
  &__info,
  &__list {
    margin-bottom: 40px;
  }
  &__text {
    font-weight: 300;
    font-size: 15px;
    line-height: 28px;
    color: #333333;
  }
  &__tel {
    font-weight: 300;
    font-size: 26px;
    line-height: 36px;
    color: #3db565;
  }
  &__link {
    font-weight: 600;
    color: #3db565;
    text-transform: uppercase;
  }
}

@media screen and(max-width: 768px) {
  .contacts {
    text-align: center;
    padding: 40px 0 30px 0;
    &__item {
      margin-bottom: 20px;
    }
  }
}

@media screen and(max-width: 576px) {
  .contacts {
    &__title {
      margin-bottom: 20px;
    }
    &__caption {
      margin-bottom: 15px;
    }
    &__info,
    &__list {
      margin-bottom: 20px;
    }
  }
}

</style>