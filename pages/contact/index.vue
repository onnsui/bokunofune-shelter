<template>
  <div class="contact">
    <div class="contact__title">お問い合わせ</div>
    <div class="contact__box">
      <div class="contact__wrapper">
        <form
          name="contactform"
          method="POST"
          data-netlify="true">
          <input
            type="hidden"
            name="form-name"
            value="contactform">
          <div class="contact__form-wrapper">
            <label class="name">お名前</label>
            <el-input
              v-model="name"
              name="name"
              placeholder="お名前"/>
          </div>
          <div class="contact__form-wrapper">
            <label class="mail">Email</label>
            <el-input
              v-model="email"
              name="email"
              placeholder="メールアドレス"/>
          </div>
          <div class="contact__form-wrapper last">
            <label class="message">メッセージ</label>
            <el-input
              :rows="3"
              v-model="remark"
              name="remark"
              type="textarea"
              placeholder="自由に入力して下さい"/>
          </div>
          <div
            slot="footer"
            class="dialog-footer">
            <el-button
              type="primary"
              native-type="submit"
              @click="dialogVisible = false">送信
            </el-button>
          </div>
        </form>
      </div>
    </div>
    <!--<div class="contact__button">-->
    <!--TICKET-->
    <!--</div>-->
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      remark: '',
    }
  },
  methods: {
    handleClose(done) {
      this.$confirm('Are you sure to close this dialog?')
        .then(_ => {
          done()
        })
        .catch(_ => {})
    },
  },
}
</script>

<style lang="scss" scoped>
.contact {
  margin: 35px 0;
  min-height: 70vh;
  &__box {
    width: 70%;
    margin: 0 auto;
    background-color: #ededed;
    padding: 35px 80px;
  }
  &__title {
    font-size: 24px;
    font-weight: bold;
    text-align: center;
    margin-bottom: 15px;
  }
  &__form-wrapper {
    display: flex;
    align-items: center;
    margin-bottom: 10px;

    span {
      width: 20%;
      font-weight: bold;
    }
    .el-input {
      width: 30%;
      /deep/ &__inner {
        border: 1px solid #8b94a5;
      }
    }
    .el-textarea {
      width: 60%;
      /deep/ &__inner {
        border: 1px solid #8b94a5;
      }
    }
  }
}
.dialog-footer {
  margin: 2em auto 0 auto;
  width: 450px;
}
/deep/ .el-dialog {
  &__header {
    background-color: #000;
    color: #fff;
  }
  &__title {
    color: #fff;
    font-weight: bold;
  }
  &__footer {
    text-align: center;
  }
}
.el-button--primary {
  background-color: #000;
  font-weight: bold;
  width: 450px;
}
.name {
  margin-right: 5em;
}
.mail {
  margin-right: 5.5em;
}
.message {
  margin-right: 3em;
}
@media (max-width: 768px) {
  .contact__box {
    width: 90%;
    padding: 20px 35px;
  }
  .contact__form-wrapper {
    flex-direction: column;
    align-items: flex-start;
    margin-bottom: 1.5em;
    .el-input {
      width: 100%;
    }
    .el-textarea {
      width: 100%;
    }
  }
  .name {
    margin-bottom: 1em;
  }
  .mail {
    margin-bottom: 1em;
  }
  .message {
    margin-bottom: 1em;
  }
  .dialog-footer {
    margin: 2em auto 0 auto;
    width: 250px;
  }
  .el-button--primary {
    background-color: #000;
    font-weight: bold;
    width: 100%;
  }
}
</style>
