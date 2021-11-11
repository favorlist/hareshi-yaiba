<script lang="ts">
  import { onMount } from 'svelte';

  import { fade, blur, fly, slide, scale } from 'svelte/transition';
  import { quintOut, quintIn } from 'svelte/easing';

  import {
    Styles, Navbar, Container, NavbarBrand, Button, Card,
    Modal, ModalBody, ModalFooter, ModalHeader
  } from 'sveltestrap';

  let ready = false;
  onMount(() => ready = true);

  let open = false;
  const toggle = () => (open = !open);
</script>

<Styles />

<Navbar dark expand="md">
  <NavbarBrand href="https://hareshi.net/">
    <img src="img/hareshichan-white.png" alt="hareshi" style="max-height:28px;" />
  </NavbarBrand>
</Navbar>

<Container>
  <div class="text-center">
    {#if ready}
      <div in:scale="{{ delay: 500 }}">
        <img
          class="img-fluid" src="img/m-hero.png" alt="ดู Kimetsu no Yaiba ที่ AIS PLAY"
          style="max-height:280px;padding:20px;padding-left:30px;padding-right:30px;"
        />
      </div>

      <div in:blur="{{ delay: 700 }}" class="mt-3 mb-5">
        <div class="row justify-content-center">
          <div class="col-md-6 col-lg-4">
            <Card class="bg-transparent py-2" style="border:2px solid #544f51; border-radius:16px;">
              <p class="m-0 p-0" style="font-size:16pt; font-weight:500;">ผู้เข้าร่วมทั้งหมด</p>
              <p class="m-0 p-0" style="font-size:48pt; font-weight:700; color:#f3aec0; line-height:70px;">
                10,000 <sup style="font-size:12pt; font-weight:400; color:#fefefe;">ท่าน</sup>
              </p>
              <p class="m-0 p-0" style="font-size:14pt; font-weight:500;">อยากดูดาบพิฆาตอสูรที่ AIS PLAY</p>
            </Card>
          </div>
        </div>
      </div>

      <div in:fade="{{ delay: 1000 }}" class="my-5">
        <Button size="lg" class="px-5 vote-btn" on:click={toggle}>
          <b>ร่วมโหวต</b>
        </Button>
      </div>

      <div class="my-5" in:fade="{{ delay: 1200 }}">
        <div class="row justify-content-center">
          <div class="col-md-6 col-lg-4 text-center">
            <p class="mb-2"><b>Presented by</b></p>
            <a href="https://hareshi.net/"><img src="img/hareshichan-white.png" alt="hareshi" style="max-height:26px;margin:10px;" /></a>
            <a href="https://aisplay.ais.co.th/portal/" target="_blank"><img src="img/aisplay.png" alt="ais play" style="max-height:26px;margin:10px;" /></a>
            <br/>
            <p class="mt-4 mb-2"><b>Powered by</b></p>
            <a href="https://www.facebook.com/thefavorlist" target="_blank"><img src="img/Folder_1s.png" alt="favorlist" style="max-height:26px;margin:10px;" /></a>
          </div>
        </div>
      </div>

      <div class="my-5" in:fade="{{ delay: 1300 }}">
        <div class="row justify-content-center">
          <div class="col-md-6 col-lg-4 text-center">
            <h5>เรื่องย่อ Kimetsu no Yaiba: Yuukaku-hen</h5>
            <p>
              Tanjirou, Zenitsu, and Inosuke, aided by the Sound Hashira Tengen Uzui, travel to Yoshiwara red light district to hunt down a demon that has been terrorizing the town.
              <br/>(Source: MyAnimeList)
            </p>

            <img class="img-fluid d-xl-none my-3" src="img/117641.jpg" alt="yaiba key visual" />

            <p class="mb-0"><b>เริ่มฉาย:</b> 5 ธันวาคม 2021</p>
            <p class="mb-0"><b>สตูดิโอ:</b> ufotable</p>
            <p><b>ผู้กำกับ:</b> Sotozaki Haruo</p>
          </div>
        </div>
      </div>
    {/if}
  </div>
</Container>

{#if ready}
  <div class="d-none d-xl-block" style="position:fixed;left:0px;bottom:0px;" in:slide="{{ delay: 1000 }}">
    <img class="d-none d-xl-block" src="img/hareshikun.png" alt="hareshi-kun" style="height:450px;-webkit-transform: scaleX(-1);transform: scaleX(-1);" />
  </div>

  <div class="d-none d-xl-block" style="position:fixed;right:48px;bottom:0px;" in:slide="{{ delay: 1500 }}">
    <a href="https://www.hareshi.net/browse/anime/129874" target="_blank" style="text-decoration:none; color:white;">
      <img class="d-none d-xl-block" src="img/117641.jpg" alt="yaiba key visual" style="height:300px;" />
      <div class="text-center" style="padding:10px; background-color:#ff769d;">
        ➤ ดูข้อมูลอนิเมะ ที่ Hareshi
      </div>
    </a>
    <a href="https://anime.favorlist.net/" target="_blank" style="text-decoration:none; color:#f7f7f7;">
      <div class="text-center" style="padding:10px; background-color:#20d98d;">
        ➤ โหวตเรื่องนี้ ที่ FavorList
      </div>
    </a>
  </div>
{/if}

<Modal centered isOpen={open} {toggle}>
  <ModalHeader {toggle}>Modal title</ModalHeader>
  <ModalBody>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
    tempor incididunt ut labore et dolore magna aliqua.
  </ModalBody>
  <ModalFooter>
    <Button color="primary" on:click={toggle}>Do Something</Button>
    <Button color="secondary" on:click={toggle}>Cancel</Button>
  </ModalFooter>
</Modal>