# Hover Card Blur Effect

> Hiệu ứng CSS thuần — hover vào card nào thì card đó hiện rõ, các card còn lại tự động blur mờ dần.

## Demo

Mở file [`index.html`](./index.html) trực tiếp trên trình duyệt — không cần server.

## Hiệu ứng bao gồm

| Thành phần | Hiệu ứng |
|---|---|
| **Card không hover** | Blur mờ + giảm opacity + thu nhỏ nhẹ |
| **Card đang hover** | Hiện rõ, nổi lên nhẹ (`scale 1.01`) |
| **Ảnh** | Zoom `×1.04` + sáng lên |
| **Tiêu đề** | Gạch chân cam trải từ trái → phải |
| **Mô tả** | Opacity giảm nhẹ |
| **Bảng điều chỉnh** | Kéo slider để thay đổi blur / opacity / tốc độ realtime |
| **Dark mode** | Toggle sáng / tối |

## Kỹ thuật

**CSS thuần — không dùng JavaScript.**
Sử dụng selector `:has()` (CSS Level 4):

```css
/* Khi grid có card nào đang hover → blur tất cả */
.posts-grid:has(.post-card:hover) .post-card {
  opacity  : 0.3;
  filter   : blur(5px);
  transform: scale(0.98);
  transition: opacity 0.4s ease, filter 0.4s ease, transform 0.4s ease;
}

/* Chỉ card đang hover → hiện rõ */
.posts-grid:has(.post-card:hover) .post-card:hover {
  opacity  : 1 !important;
  filter   : blur(0px) !important;
  transform: scale(1.01) !important;
}
```

## Áp dụng cho WordPress / Bricks Builder

Thay class trong demo bằng class thực tế của Bricks:

| Demo class | Bricks class |
|---|---|
| `.posts-grid` | `#brxe-kpdjbo` (ID của div cha) |
| `.post-card` | `.brxe-rqolzu` (query loop item) |
| `.post-image-link img` | `.brxe-zidddg img` |
| `.post-title` | `.brxe-lohmkx` |
| `.post-excerpt` | `.brxe-oilqyr` |

Trong Bricks element Custom CSS, dùng `%root%` thay cho ID element:

```css
%root%:has(.brxe-rqolzu:hover) .brxe-rqolzu {
  opacity: 0.3;
  filter : blur(5px);
}
```

## Tùy chỉnh nhanh

```css
:root {
  --blur-amount : 5px;   /* Độ blur */
  --dim-opacity : 0.3;   /* Độ mờ (0 = tàng hình, 1 = bình thường) */
  --speed       : 0.4s;  /* Tốc độ animation */
}
```

---

*Tạo cho [nguyenthuyvy.com](https://nguyenthuyvy.com)*
